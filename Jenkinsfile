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
                pwd
                '''
                echo 'Testing test nieeh..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}