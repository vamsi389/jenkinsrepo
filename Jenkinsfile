pipeline {
  agent any

  environment {
    APP_NAME = 'my-first-app'
  }
  stages{
    stage('Test') {
      steps {
        echo "Welcome to Jenkins"
        sh 'echo "$(whoami)"'
        echo "$APP_NAME"
      }
    }
    stage('Build') {
      steps {
        sh 'sudo touch /home/ubuntu/jenkins.txt'
      }
    }
  }
}
