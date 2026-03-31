pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git 'https://github.com/YOUR_USERNAME/student-feedback-devops.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t feedback-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop feedback-app || true
                docker rm feedback-app || true
                docker run -d -p 5000:5000 --name feedback-app feedback-app
                '''
            }
        }
    }
}