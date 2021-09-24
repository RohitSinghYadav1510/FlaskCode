pipeline {
   agent {
     docker {
        image 'python:3.9.4'
        }
     }
  stages {
     stage('Build') {
 
            steps {
              sh 'python -m pip install --upgrade pip'
              sh 'pip install -r requirements.txt'
              }
         }
     stage('Test Application') {
    
            steps {
              sh 'python test.py'
              }
            post {
              always {
                 junit 'test-reports/*.xml'
               }
            }    
        }
    stage('Run Application') {
 
            steps {
              sh 'python app.py'
              }
         }
    }
}