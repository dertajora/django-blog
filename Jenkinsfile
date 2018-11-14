pipeline {
    agent {
        docker { image 'python:3.6' }
    }
    stages {
        stage('Build') {
            steps {
                sh "pip install -r requirements.txt"
                echo 'Building nieeh..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing test..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}