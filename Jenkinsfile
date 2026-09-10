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
        APP_NAME = payment-api
    }

stages {
    stage('Test') {
        steps {
            sh 'pwd'
            sh 'sudo ls -ltrh'
            sh 'sudo git log -1'
        }
    }

    stage('Build') {
        steps {
            sh 'sudo python3 -m venv .venv'
            sh 'sudo source .venv/bin/activate'
            sh 'sudo pip install -r requirements.txt'
            sh 'pytest test_app.py'
        }
    }
}
}
        
