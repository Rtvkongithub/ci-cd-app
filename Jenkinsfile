pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Rtvkongithub/ci-cd-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t myapp:latest .'
                }
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests (optional)'
            }
        }

        stage('Deploy') {
            steps {
                script {
                    sh 'docker stop myapp || true && docker rm myapp || true'
                    sh 'docker run -d --name myapp -p 8081:8080 myapp:latest'
                }
            }
        }
    }
}
