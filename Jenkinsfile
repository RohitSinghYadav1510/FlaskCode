pipeline {
   agent none
    options {
        skipStagesAfterUnstable()
    }
  stages {
     stage('Build') {
            agent {
                docker {
                    image 'rohit1015/flaskimg:v1'
                }
            }
            steps {
              sh 'pip install -r requirements.txt'
              }

     stage('Test Application') {
            agent {
                docker {
                    image 'rohit1015/flaskimg:v1'
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
    stage('Run Application') {
            agent {
                docker {
                    image 'rohit1015/flaskimg:v1'
                }
            }
            steps {
              sh 'python app.py'
              }
        }
   }
}