pipeline {
    agent any
    stages {
        stage('Clone') {
            steps {
                sh 'rm -rf chaperootodo_client'
                sh 'git clone https://gitlab.com/qacdevops/chaperootodo_client.git'
            }
        }
        stage('Docker') {
            steps {
            sh 'sudo apt-get update'
            sh 'curl https://get.docker.com | sudo bash -y'    
            sh 'sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose"'
            sh 'sudo chmod +x /usr/local/bin/docker-compose'
            }
        }
        stage('Deploy') {
            steps {
            sh 'sudo docker-compose pull && sudo -E DB_PASSWORD=${DB_PASSWORD} docker-compose up -d'
            }
        }
    }
}