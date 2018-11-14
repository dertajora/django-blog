pipeline {
    agent {
        docker { image 'python:3.6' }
    }

    def installed = fileExists 'bin/activate'

    stages {
        stage('Build') {
            def installed = fileExists 'bin/activate'
            
            steps {
                if (!installed) {
                    sh 'virtualenv --no-site-packages .'
                }  
                sh 'python --version'
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