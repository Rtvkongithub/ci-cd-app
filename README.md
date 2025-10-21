# ci-cd-app
ci/cd learning

Restarting my Jenkins
<img width="1110" height="893" alt="image" src="https://github.com/user-attachments/assets/5095f479-ba5e-4bbd-9c4c-b199602a41e7" />

Project Structure
myapp/
 ├── app.py
 ├── Dockerfile
 ├── requirements.txt
 └── Jenkinsfile

Jenkinsfile
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

Step 2: Created jenkins file
Open Jenkins → New Item
Name: Flask-CI-CD
Choose: Pipeline
Definition → Pipeline script from SCM
SCM → Git
Repository URL → https://github.com/Rtvkongithub/ci-cd-app
Branch → main
Save.
<img width="1920" height="919" alt="image" src="https://github.com/user-attachments/assets/9fd1ae9a-3ddd-48ec-b254-b67860fb51d6" />


Step 3: Build the Pipeline
Build Now → Jenkins will:
Clone your repo
Build Docker image
Deploy your app
 → open your browser:
👉 http://localhost:8080
Hello from Jenkins CI/CD Pipeline!
<img width="1920" height="1053" alt="image" src="https://github.com/user-attachments/assets/97e7ea52-1350-4d5c-9d9a-f19b62443442" />

