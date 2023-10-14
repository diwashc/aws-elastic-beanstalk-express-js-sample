pipeline {
     agent { docker { image 'node:16'
             args '-v /var/run/docker.sock:/var/run/docker.sock' 
	     args "-v ${WORKSPACE}:/var/jenkins_home/workspace/21255001_Project2_Pipeline:rw,z"
	     args "-v ${WORKSPACE}@tmp:/var/jenkins_home/workspace/21255001_Project2_Pipeline@tmp:rw,z"
         }
     }

     stages {
         stage('Build') {
             steps {
                 sh 'npm install --save' 
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
