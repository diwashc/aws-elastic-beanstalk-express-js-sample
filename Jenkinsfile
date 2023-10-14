pipeline {
     agent { docker { 
	     image 'node:16'
             args '-u 0:0'
         }
     }

     stages {
         stage('Build') {
             steps {
                 sh 'npm install --save' 
             }
         }
     }
 }
