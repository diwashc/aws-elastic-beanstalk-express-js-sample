pipeline {
    agent {
        docker {
            image 'docker:20' // Use a Docker image with Docker installed
            args '-v /var/run/docker.sock:/var/run/docker.sock' // Mount the Docker socket
        }
    }
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm // Checkout your source code
            }
        }

        stage('Build') {
            steps {
                sh 'docker pull node:16' // Pull the Node 16 image
                sh 'docker run --rm node:16 npm install' // Run npm install inside a Docker container
            }
        }
        
        stage('Check Node.js and npm') {
            steps {
                sh 'docker run --rm node:16 node -v' // Check Node.js version
                sh 'docker run --rm node:16 npm -v' // Check npm version
            }
        }
    }
    
    post {
        success {
            echo 'Build and npm install successful'
        }
        failure {
            echo 'Build or npm install failed'
        }
    }
}
