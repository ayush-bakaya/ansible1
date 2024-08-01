pipeline {
    agent any

   
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
                   
                )
            }    
        }    
    }
}
