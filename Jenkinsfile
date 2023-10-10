pipeline {
    agent {
        docker {
            image 'node:16' // Use Node 16 Docker image as the build agent
            args '-v /var/run/docker.sock:/var/run/docker.sock' // Mount Docker socket for Docker-in-Docker
        }
    }
    
    stages {
        stage('Build') {
            steps {
                sh 'npm install --save' // Run npm install --save
            }
        }
    }
    
    post {
        success {
            echo 'Build successful!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}

