pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git 'https://github.com/jamesarochristober/Demo-backend-code.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t django-app .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh '''
                docker stop django-container || true
                docker rm django-container || true
                '''
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 8000:8000 --name django-container django-app'
            }
        }
    }
}
