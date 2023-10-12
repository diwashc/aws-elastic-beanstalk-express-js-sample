pipeline {
    agent {
        docker {
            image 'node:16' // Use Node 16 Docker image as the build agent
            args '-u root'  // Use root user to avoid permission issues
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
