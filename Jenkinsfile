pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '''
                    docker build -t angular-basic-app:latest .
                '''
            }
        }

        stage('Run Angular App') {
            steps {
                sh '''
                    docker rm -f angular-basic-container || true
                    docker run -d \
                      --name angular-basic-container \
                      -p 5200:80 \
                      angular-basic-app:latest
                '''
            }
        }
    }
}
