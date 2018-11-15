pipeline {
    agent {
        docker { image 'python:3.6' }
    }

    stages {
        stage('Build') {
            steps {
                sh '''
                python --version
                docker --version
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