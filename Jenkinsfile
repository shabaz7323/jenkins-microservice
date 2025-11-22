pipeline {
    agent any

    environment {
        APP_NAME = "sample-app"
    }

    stages {

        stage('Install Dependencies (Node using Docker)') {
            steps {
                sh '''
                echo "Running npm install inside Node Docker container..."

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
                echo "Building Docker Image..."
                docker build -t $APP_NAME .
                '''
            }
        }

        stage('Docker Push') {
            steps {
                echo "Push to DockerHub here"
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                echo "Deploy to Kubernetes here"
            }
        }
    }

    post {
        success {
            echo "Pipeline Completed Successfully!"
        }
        failure {
            echo "Pipeline Failed! Check the logs."
        }
    }
}
