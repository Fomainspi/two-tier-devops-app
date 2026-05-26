pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                echo 'Cloning repository from GitHub...'
            }
        }

        stage('Build Application') {
            steps {
                echo 'Building Docker Compose services...'
                sh 'docker compose build'
            }
        }

        stage('Deploy Application') {
            steps {
                echo 'Starting application containers...'
                sh 'docker compose up -d'
            }
        }

    }
}