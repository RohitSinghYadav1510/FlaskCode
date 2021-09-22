pipeline {
  agent { 
    docker { 
       image 'python:3.9.4' 
       } 
    }

  stages {
    stage('Git Fetch') {
      steps {
        git 'https://github.com/RohitSinghYadav1510/FlaskCode.git'
      }
    }

    stage('build') {
      steps {
        sh 'pip install -r requirements.txt'
      }
    }

    stage('test') {
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
