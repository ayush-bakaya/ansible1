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
                    installation: 'Ansible',
                    disableHostKeyChecking: true,
                    installation: 'Ansible',
                    inventory: 'dev.inv',
                    playbook: 'nginx.yaml',
                   
                )
            }    
        }    
    }
}
