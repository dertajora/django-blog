pipeline {
    agent {
        docker { image 'python:3.6' }
    }
    stages {
        stage('Build') {
            steps {
                sh '''
                    whoami
                    python --v
                '''
                echo 'Building nieeh..'
            }
        }
        stage('Test') {
            steps {
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