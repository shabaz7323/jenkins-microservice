pipeline {
    agent any
    
    stages {
        stage('Build with Node') {
            steps {
                script {
                    docker.image('node:18').inside {
                        sh 'npm install'
                    }
                }
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t sample-app .'
            }
        }

        stage('Docker Push') {
            steps {
                echo 'Push to DockerHub here'
            }
        }

        stage('Deploy to K8s') {
            steps {
                echo 'kubectl apply -f deployment.yaml'
            }
        }
    }
}
