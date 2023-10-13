pipeline {
    agent {
        docker {
            image 'docker:20'
            args '--privileged -v /var/run/docker.sock:/var/run/docker.sock'
        }
    }
    stages {

stage('Run Docker Commands') {
    steps {
        script {
            sh 'sudo docker --version' // Use sudo to run Docker commands as root
        }
    }
}
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                sh 'docker build -t myapp .'
            }
        }
stage('Install Docker') {
    steps {
        sh 'curl -fsSL https://get.docker.com -o get-docker.sh'
        sh 'sh get-docker.sh'
        sh 'usermod -aG docker jenkins'  // Add Jenkins to the Docker group
        sh 'docker --version'  // Verify Docker installation
    }
}
stage('Add Jenkins to Docker Group') {
    steps {
        sh 'usermod -aG docker jenkins'
    }
}
        // Add more stages as needed
    }
    post {
        success {
            echo 'Build successful'
        }
        failure {
            echo 'Build failed'
        }
    }
}
