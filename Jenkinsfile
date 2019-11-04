pipeline {
  agent { docker { image 'python:3.7.2' } }
  stages {
    stage('build') {
      steps {
        sh 'sudo chown -R root /home/$USERNAME/.cache/pip/'
        sh 'sudo chown -R root /home/$USERNAME/.cache/pip/http/'
        sh 'sudo pip install -r requirements.txt'
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
