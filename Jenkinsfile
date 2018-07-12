pipeline {
  agent {
    label 'jdk8'
  }
  stages {
    stage('Say Hello') {
      steps {
        sh '''echo "Hello ${MY_NAME}!"
                # echo "or is it ${params.Name}?"
                echo "${TEST_USER_USR}"
                echo "${TEST_USER_PSW}"
             '''
      }
    }
    stage('Deploy') {
      options {
        timeout(time: 30, unit: 'SECONDS')
      }
      input {
        message 'Which Version?'
        id 'Deploy'
        parameters {
          choice(name: 'APP_VERSION', choices: '''v1.1\nv1.2\nv1.3''', description: 'What to deploy?')
        }
      }
      steps {
        echo "Deploying ${APP_VERSION}."
      }
    }
  }
  post {
    aborted {
      echo 'Why didn\'t you push my button?'
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
