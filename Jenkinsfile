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
                sh 'python app.py'
            }
        }
    }
}