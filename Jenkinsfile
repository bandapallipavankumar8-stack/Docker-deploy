pipeline {
    agent any
    stages {
        stage('Checkout') { steps { checkout scm } }
        stage('Build') { steps { sh 'docker build -t webapp .' } }
        stage('Deploy') { 
            steps { 
                sh 'docker stop webapp-run || true'
                sh 'docker rm webapp-run || true'
                sh 'docker run -d --name webapp-run -p 8080:80 webapp' 
            } 
        }
    }
}