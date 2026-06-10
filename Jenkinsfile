pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/velaga527bhavya/Projects1.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t cicd-demo .'
            }
        }

        stage('Run Docker Container') {
            steps {
                bat '''
                docker stop cicd-demo-container || exit 0
                docker rm cicd-demo-container || exit 0
                docker run -d --name cicd-demo-container -p 8080:80 cicd-demo
                '''
            }
        }

    }
}