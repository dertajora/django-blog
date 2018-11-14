pipeline {
    agent {
        docker { image 'python:3.6' }
    }

    stages {
        stage('Build') {
            steps {
                sh '''
                virtualenv --no-site-packages .
                python --version
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