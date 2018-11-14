pipeline {
    agent {
        docker { image 'python:3.6' }
    }

    stages {
        stage('Build') {
            steps {
                sh '''
                sudo pip install virtualenv
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