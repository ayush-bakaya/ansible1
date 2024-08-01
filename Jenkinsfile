pipeline {
    agent any

    environment {
        ANSIBLE_SSH_PASS = credentials('ssh-password') // Jenkins credentials ID for SSH password
        ANSIBLE_BECOME_PASS = credentials('ssh-password') // Jenkins credentials ID for sudo password
    }
    stages {
        stage("SCM checkout") {
            steps {
                git branch: 'main', url: 'https://github.com/ayush-bakaya/ansible1.git'
            }
        }
        
        stage("Execute Ansible") {
            steps {
                ansiblePlaybook(
                    credentialsId: 'private-key', // Jenkins credentials ID for SSH private key
                    disableHostKeyChecking: true,
                    installation: 'Ansible',
                    inventory: 'dev.inv',
                    playbook: 'nginx.yaml',
                    extraVars: [
                        ansible_ssh_pass: "${ANSIBLE_SSH_PASS}",
                        ansible_become_pass: "${ANSIBLE_BECOME_PASS}"
                    ]
                )
            }    
        }    
    }
}
