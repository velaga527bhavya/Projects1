pipeline {

    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t cicd-demo .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh '''
                docker stop cicd-demo || true
                docker rm cicd-demo || true
                docker run -d --name cicd-demo -p 8080:80 cicd-demo
                '''
            }
        }

    }

    post {
        success {
            echo 'Pipeline executed successfully!'
        }

        failure {
            echo 'Pipeline failed!'
        }
    }
}