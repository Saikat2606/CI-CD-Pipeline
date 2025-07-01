pipeline {
    agent any
    stages {
        stage('Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/Saikat2606/CI-CD-Pipeline.git'
            }
        }
        stage('Run Ansible') {
            steps {
                sh 'ANSIBLE_HOST_KEY_CHECKING=False ansible-playbook -i inventory.ini playbook.yml'
            }
        }
    }
}


