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

        stage('Install Dependencies') {
            steps {
                sh 'sudo apt-get update'
                sh 'sudo apt install python3-requirements.txt
            }
        }

        stage('Test') {
            steps {
                sh 'python3 -m pytest -v'
            }
        }

        stage('Build Artifact') {
            steps {
                sh 'tar -czf myapp-${BUILD_NUMBER}.tar.gz app.py'
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: '*.tar.gz'
            }
        }
    }
}
