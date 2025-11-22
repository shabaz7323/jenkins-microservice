pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/shabaz7323/jenkins-microservice.git'
            }
        }

        stage('Build') {
            steps {
                sh 'npm install'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t sample-app .'
            }
        }

        stage('Docker Push') {
            steps {
                echo 'Push to registry here'
            }
        }

        stage('Deploy to K8s') {
            steps {
                echo 'kubectl apply -f deployment.yaml'
            }
        }
    }
}
