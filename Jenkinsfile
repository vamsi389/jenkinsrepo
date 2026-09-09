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

        stage('Create Virtual Environment') {
            steps {
                sh 'python3 -m venv .venv'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '.venv/bin/pip install -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                sh '.venv/bin/python -m pytest -v'
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
