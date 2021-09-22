pipeline {

  stages {
    stage('Git Fetch') {
      steps {
        git 'https://github.com/RohitSinghYadav1510/FlaskCode.git'
      }
    }

    stage('RUN APP') {
      agent {
          docker {
              image 'flaskami:v1' 
           }
        } 
      steps {
        sh 'python app.py'
      }
    }
    stage('Test APP') {
      agent {
          docker {
              image 'flaskami:v1' 
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
