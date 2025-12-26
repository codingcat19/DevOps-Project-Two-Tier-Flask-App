pipeline {
    agent any 
    stages {
        stage("Code Clone") {
            steps {
                git branch: 'main', url: 'https://github.com/codingcat19/DevOps-Project-Two-Tier-Flask-App.git'
            }
        }

        stage("Build Image") {
            steps {
                sh 'docker build -t codingcat19/my-flask-app .'
            }
        }

        stage("Deploy with docker compose") {
            steps {
                sh '''
                docker compose down || true
                docker compose up -d --build
                '''
            }
        }

        stage("Cleanup") {
            steps {
                echo 'Cleaning up old docker resources...'
                sh 'docker system prune -f'
            }
        }
    }
}