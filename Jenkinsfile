pipeline {
  agent any

  stages{
    stage('Test') {
      steps {
        echo "Welcome to Jenkins"
        sh 'echo "$(whoami)"'
      }
    }
    stage('Build') {
      steps {
        sh 'sudo touch /home/ubuntu/jenkins.txt'
      }
    }
  }
}
