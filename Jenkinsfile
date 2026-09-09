pipeline {
    agent any

    options {
        skipDefaultCheckout()
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Verify') {
            steps {
                sh 'pwd'
                sh 'ls -la'
                sh 'git log -1 --oneline'
            }
        }
    }
}
