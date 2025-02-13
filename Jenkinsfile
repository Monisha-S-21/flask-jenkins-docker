pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/Monisha-S-21/flask-jenkins-docker.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    bat 'docker build -t flask-app .'
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    bat 'docker run -d -p 5000:5000 --name flask-container flask-app'
                }
            }
        }

        stage('Clean Up') {
            steps {
                script {
                    bat 'docker stop flask-container || exit 0'
                    bat 'docker rm flask-container || exit 0'
                    bat 'docker rmi flask-app || exit 0'
                }
            }
        }
    }
}
