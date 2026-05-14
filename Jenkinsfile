pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                echo 'Cloning repository...'
                git branch: 'main', url: 'https://github.com/jeellabs/DevOps-Project-cicd-Two-Tier-Flask-App.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image...'
                sh 'docker build -t flask-app:latest .'
            }
        }

        stage('Deploy with Docker Compose') {
            steps {
                echo 'Deploying...'
                sh 'docker compose down || true'
                sh 'docker compose up -d --build'
            }
        }

    }

    post {
        success {
            echo 'Deployment Successful!'
        }
        failure {
            echo 'Deployment Failed!'
        }
    }
}
