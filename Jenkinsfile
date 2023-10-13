pipeline {
    agent {
        docker {
            image 'node:16' // Use Node 16 Docker image as the build agent
            args '--user jenkins:jenkins'  // Specify the Jenkins user within the container
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
                sh 'npm install --save' // Run the npm install command
            }
        }
        
        stage('Check Node.js and npm') {
            steps {
                sh 'node -v'
                sh 'npm -v'
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
