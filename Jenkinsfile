pipeline {
  agent {
    label 'jdk8'
  }
  stages {
    stage('Say Hello') {
      parallel {
        stage('Say Hello') {
          steps {
            echo 'Say Hello'
          }
        }
        stage('Hello bash') {
          steps {
            sh 'echo "Hello ${MY_NAME}!"'
          }
        }
      }
    }
  }
  environment {
    MY_NAME = 'mary'
  }
}