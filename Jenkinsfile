pipeline {
    agent any
    stages {
        stage('Checkout') { 
            steps { 
                checkout scm 
            } 
        }
        stage('Build') { 
            steps { 
                sh 'docker build -t webapp .' 
            } 
        }
        stage('Deploy') { 
            steps { 
                sh 'docker stop webapp-run || true'
                sh 'docker rm webapp-run || true'
                // Changed host port from 8080 to 8085 to avoid conflicts
                sh 'docker run -d --name webapp-run -p 8085:80 webapp' 
            } 
        }
    }
}
