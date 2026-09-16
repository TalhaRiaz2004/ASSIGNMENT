# Created by: TALHA BIN RIAZ
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/<your-username>/<your-repo>.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'python3 -m venv venv'
                sh './venv/bin/pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                sh './venv/bin/pytest'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-sample-app .'
            }
        }
    }

    post {
        success {
            echo 'Build, tests, and Docker image all succeeded.'
        }
        failure {
            echo 'Build failed — check the stage logs above.'
        }
    }
}
