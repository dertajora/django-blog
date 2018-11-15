pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh '''
                virtualenv venv
                source venv/bin/activate
                python -r requirements.txt
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