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
        sh 'touch /home/ubuntu/jenkins.txt'
      }
    }
  }
}
