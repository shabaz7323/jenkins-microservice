pipeline {
    agent any

    stages {

        stage('Install Node.js') {
            steps {
                sh '''
                # Install Node.js 18 manually inside Jenkins container
                curl -fsSL https://deb.nodesource.com/setup_18.x | bash -
                apt-get install -y nodejs
                node -v
                npm -v
                '''
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
