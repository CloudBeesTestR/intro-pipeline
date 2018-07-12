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
            sh '''echo "Hello ${MY_NAME}!"
                  # echo "or is it ${params.Name}?"
                  echo "${TEST_USER_USR}"
                  echo "${TEST_USER_PSW}"
               '''
          }
        }
      }
    }
    stage('Deploy') {
      input {
        message "Should we continue?"
      }
      steps {
        echo "Continuing with deployment"
      }
    }
  }
  environment {
    MY_NAME = 'mary'
    TEST_USER = credentials('test-user')
  }
  parameters {
    string(name: 'Name', defaultValue: 'whoever you are', description: 'Who should I say hi to?')
  }
}
