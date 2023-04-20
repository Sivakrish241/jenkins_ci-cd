pipeline {
    agent any

    stages {
        stage('Clone Docker code') {
            steps {
                git 'https://github.com/Sivakrish241/jenkins_ci-cd.git'
                sh 'cp -r /var/lib/jenkins/workspace/jenkins_ci-cd /home/ubuntu/'
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
                sh 'docker build -t my-node-app /home/ubuntu/jenkins_ci_cd/Dockerfile'
            }
        }

        stage('Start container') {
            steps {
                sh 'docker run -d --name my-node-app -p 3000:3000 my-node-app'
            }
        }
    }
}
