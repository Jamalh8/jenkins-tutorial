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
            sh 'curl https://get.docker.com | sudo bash'    
            sh 'sudo curl -L "https://github.com/docker/compose/releases/download/1.27.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose'
            sh 'sudo chmod +x /usr/local/bin/docker-compose'
            }
        }
        stage('Deploy') {
            steps {
            sh 'export DB_PASSWORD=12345'    
            sh 'sudo docker-compose pull -f && sudo -E DB_PASSWORD=${DB_PASSWORD} docker-compose up -d'
            }
        }
    }
}
