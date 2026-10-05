pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                 git branch: 'main', url: 'https://github.com/Vishnuka144/Jenkins-CICD-Pipeline-Nodejs.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'npm test'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t jenkins-node-app .'
            }
        }

        stage('Run Docker Container') {
            steps {
                bat 'docker run -d -p 3000:3000 --name jenkins-node-app jenkins-node-app'
            }
        }
    }

    post {
        always {
            echo 'Cleaning up...'
           // sh 'docker rm -f jenkins-node-app || true'
        }
    }
}
