pipeline {
   agent {
     docker {
        image 'rohit1015/flaskimg:v1'
        }
     }
  stages {
     stage('Build') {
            
            steps {
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