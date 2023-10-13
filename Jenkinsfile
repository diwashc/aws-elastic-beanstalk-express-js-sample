pipeline {
    agent any

    stages {
        stage('Install Docker') {
            steps {
                sh 'docker --version' // Check Docker version without using sudo
            }
        }
    }

    post {
        success {
            echo 'Pipeline succeeded'
        }
        failure {
            echo 'Pipeline failed'
        }
    }
}
