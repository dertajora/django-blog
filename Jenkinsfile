pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh '''
                pwd
                virtualenv venv
                . venv/bin/activate
                pip3 install -r requirements.txt
                deactivate
                '''
                echo 'Building nieeh..'
            }
        }
        stage('Test') {
            steps {
                sh '''
                . venv/bin/activate
                python3 manage.py test test/
                deactivate
                '''
                echo 'Testing nieeh..'
            }
        }
        input "Deploy to prod?"
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}