pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                sh 'echo passed'
                // Check out the source code from Git
                // git branch: 'main', url: 'git clone https://github.com/iam-rajkumar96/nginx-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                // Build the Docker image
                script {
                   sh 'cd nginx-project/ && docker build -t notes-app .'
                }
            }
        }
        
        stage('Deploy to Nginx') {
            steps {
                // Deploy the Docker container using Nginx
                sh 'docker run -d -p 8000:8000 nginx-app:latest'
                sh 'cd mynotes/build && cp -r * /var/www/html'
                sh 'Curl -L http://127.0.0.1:8000'
            }
        }
    }
}
