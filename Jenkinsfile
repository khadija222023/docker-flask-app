pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/khadija222023/docker-flask-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t flask-app:v1 .'
            }
        }

        stage('Stop Existing Container') {
            steps {
                sh '''
                docker stop flask-container || true
                docker rm flask-container || true
                '''
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker run -d \
                --name flask-container \
                -p 5000:5000 \
                flask-app:v1
                '''
            }
        }
    }
}