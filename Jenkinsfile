pipeline {
  agent none

  stages {
    stage('Git Fetch') {
      steps {
        git 'https://github.com/RohitSinghYadav1510/FlaskCode.git'
      }
    }
    stage('Build Docker Image') {
      steps {
         sh "docker build -t flask-app:v1 ."
        }
    }
    stage('build') {
       agent {
          docker {
              image 'flask-app:v1' 
           }
        }           
      steps {
        sh 'pip install -r requirements.txt'
      }
    }

    stage('test') {
      agent {
          docker {
              image 'flask-app:v1' 
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
