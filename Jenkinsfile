pipeline {
   agent none
    options {
        skipStagesAfterUnstable()
    }
  stages {
    stage('test') {
      agent { 
         docker { 
              image 'rohit1015/flaskami:v1' 
              } 
            }
      steps {
        sh 'python test.py'
      }
      post {
        always {
          junit 'test-reports/*.xml'
        }
      }    
    }
  }
}