pipeline {
    agent any

    stages {
        stage('Stop container') {
            steps {
                sh 'docker stop my-node-app || true'
                sh 'docker rm my-node-app || true'
            }
        }

        stage('Build image') {
            steps {
                sh 'docker build -t my-node-app .'
            }
        }

        stage('Start container') {
            steps {
                sh 'docker run -d --name my-node-app -p 3000:3000 my-node-app'
            }
        }
    }
}
