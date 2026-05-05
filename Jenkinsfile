pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/YOUR-USERNAME/YOUR-REPO.git'
            }
        }

        stage('Build Images') {
            steps {
                sh 'docker build -t backend ./backend'
                sh 'docker build -t frontend ./frontend'
            }
        }

        stage('Stop Old Containers') {
            steps {
                sh 'docker rm -f backend || true'
                sh 'docker rm -f frontend || true'
            }
        }

        stage('Run Containers') {
            steps {
                sh 'docker run -d -p 5000:5000 --name backend backend'
                sh 'docker run -d -p 3000:80 --name frontend frontend'
            }
        }
    }
}
