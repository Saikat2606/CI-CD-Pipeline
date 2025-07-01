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
                withCredentials([sshUserPrivateKey(credentialsId: 'jenkins-slave-key', keyFileVariable: 'SSH_KEY')]) {
                    sh '''
                        echo "Using SSH key from Jenkins credentials"
                        ls -l "$SSH_KEY" || echo "Key file missing"
                        chmod 600 "$SSH_KEY"
                        ansible-playbook -i inventory.ini playbook.yml --private-key="$SSH_KEY" -u ec2-user
                    '''
                }
            }
        }
    }
}

