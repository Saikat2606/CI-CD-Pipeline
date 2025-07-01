pipeline {
    agent any

    environment {
        ANSIBLE_HOST_KEY_CHECKING = 'False'
    }

    stages {
        stage('Clone') {
            steps {
                git credentialsId: 'github-pat', url: 'https://github.com/Saikat2606/CI-CD-Pipeline.git', branch: 'main'
            }
        }

        stage('Run Ansible') {
            steps {
                sh 'ansible-playbook -i inventory.ini playbook.yml --private-key=/home/ec2-user/.ssh/id_rsa'
            }
        }
    }
}

