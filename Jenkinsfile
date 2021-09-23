pipeline {
   agent none
    options {
        skipStagesAfterUnstable()
    }
  stages {
     stage('Build') {
            agent {
                docker {
                    image 'rohit1015/flaskami:v1'
                }
            }
            steps {
                sh 'python -m py_compile app.py'
                stash(name: 'compiled-results', includes: '*.py*')
            }
        }

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