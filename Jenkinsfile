pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-app .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh '''
                    docker stop devops-app || true
                    docker rm devops-app || true
                    docker run -d -p 80:80 --name devops-app devops-app
                '''
            }
        }
    }
}
