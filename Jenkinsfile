pipeline {
  agent { docker { image 'python:3.7.4' } }
  stages {
    stage('build') {
      steps {
        withEnv(["HOME=${env.WORKSPACE}"]) {
        sh 'pip uninstall -r requirements.txt'
        sh 'pip install -r requirements.txt'
        }
      }
    }
    stage('test') {
      steps {
        withEnv(["HOME=${env.WORKSPACE}"]) {
        sh 'python test.py'
        }
      }
      post {
        always {
          withEnv(["HOME=${env.WORKSPACE}"]) {
          junit 'test-reports/*.xml'
          }
        } 
      }  
    }
  }
}
