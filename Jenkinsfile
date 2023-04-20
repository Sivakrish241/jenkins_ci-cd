pipeline {
    agent any

    stages {
        stage('Stop and remove container') {
            steps {
                sh 'docker stop my-node-app || true'
                sh 'docker rm my-node-app || true'
            }
        }

        stage('Build and run container') {
            steps {
                sh 'sudo usermod -aG docker jenkins'
                sh 'sudo systemctl restart docker'
                sh 'docker build -t my-node-app .'
                sh 'docker run -d --name my-node-app -p 3000:3000 my-node-app'
            }
        }
    }
}
