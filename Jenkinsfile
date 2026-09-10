pipeline {
    agent any

    options {
        skipDefaultCheckout()
    }

    parameters {
        choice(
            name: 'Environment',
            choices: ['Dev','Prod','stage'],
            description: 'Select the target environment for deployment'
        )
    }

    environment {
        APP_NAME = 'payment-api'
        MY_SECRET = credentials('day5-demo-token')
    }

stages {

    stage('Checkout') {
        steps {
        checkout scm
        }
    }
    
    stage('Test') {
        steps {
            sh 'pwd'
            sh 'sudo ls -ltrh'
            sh 'sudo git log -1'
        }
    }

    stage('Build') {
        steps {
            sh 'sudo rm -rf .venv'
            sh 'python3 -m venv .venv'
            sh '.venv/bin/pip install -r requirements.txt'
            sh '.venv/bin/python -m pytest -v'
            sh '.venv/bin/python -m pytest test_app.py -v'
            sh 'echo "$MY_SECRET"'
        }
    }
}
}
        
