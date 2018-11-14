pipeline {
    agent {
        docker { image 'python:3.6' }
    }
    stages {
        stage('Build') {
            steps {
                sh ''' 
                    virtualenv venv --distribute
                    . venv/bin/activate 
                    pip install -r requirements.txt
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