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
                script {
                    // Run Docker-in-Docker
                    docker.image('docker:20').inside('-u root') {
                        // Pull and run Docker containers
                        sh 'docker pull node:16'
                        sh 'docker run node:16 npm install'
                    }
                }
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
