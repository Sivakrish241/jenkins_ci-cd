pipeline {
    agent any

    stages {
        stage('Clone code') {
            steps {
                dir('/home/ubuntu') {
                    git 'https://github.com/my-docker-app.git'
                }
            }
        }

        stage('Stop container') {
            steps {
                sh 'docker stop my-node-app || true'
                sh 'docker rm my-node-app || true'
            }
        }

        stage('Build image') {
            steps {
                sh 'docker build -t my-node-app /home/ubuntu/path/to/Dockerfile'
            }
        }

        stage('Start container') {
            steps {
                sh 'docker run -d --name my-node-app -p 3000:3000 my-node-app'
            }
        }
    }
}
