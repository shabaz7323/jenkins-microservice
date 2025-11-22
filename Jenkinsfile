pipeline {
    agent any

    environment {
        APP_NAME = "jenkins-microservice"
        IMAGE_NAME = "jenkins-microservice:latest"
    }

    stages {

        stage('Checkout') {
            steps {
                echo "Pulling code from GitHub..."
            }
        }

        stage('Install Dependencies (Node via Docker)') {
            steps {
                sh '''
                echo "Installing Node modules using Node Docker image..."

                docker run --rm \
                    -v "$PWD":/usr/src/app \
                    -w /usr/src/app \
                    node:18 \
                    npm install
                '''
            }
        }

        stage('Docker Build') {
            steps {
                sh '''
                echo "Building Docker image..."
                docker build -t $IMAGE_NAME .
                '''
            }
        }

        stage('Docker Push') {
            steps {
                echo "You can add DockerHub push steps here"
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                echo "You can add kubectl apply -f deployment.yaml here"
            }
        }
    }

    post {
        success {
            echo "Pipeline Completed Successfully!"
        }
        failure {
            echo "Pipeline Failed. Check errors above!"
        }
    }
}
