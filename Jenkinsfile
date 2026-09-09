pipeline {
    agent any

    options {
        skipDefaultCheckout()
    }

    parameters {
        choice(
            name: 'ENVIRONMENT',
            choices: ['dev', 'test', 'prod'],
            description: 'Select deployment environment'
        )
    }

    environment {
        APP_NAME = 'my-first-app'
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

        stage('Credential Test') {
            steps {
                withCredentials([
                    string(
                        credentialsId: 'day5-demo-token',
                        variable: 'API_TOKEN'
                    )
                ]) {
                    sh '''
                        if [ -n "$API_TOKEN" ]; then
                            echo "Credential loaded successfully"
                        else
                            echo "Credential missing"
                            exit 1
                        fi
                    '''
                }
            }
        }

        stage('Build Artifact') {
            steps {
                sh 'tar -czf ${APP_NAME}-${BUILD_NUMBER}.tar.gz app.py'
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: '*.tar.gz'
            }
        }

        stage('Summary') {
            steps {
                echo "Application: ${env.APP_NAME}"
                echo "Environment: ${params.ENVIRONMENT}"
                echo "Build Number: ${env.BUILD_NUMBER}"
            }
        }
    }
}
