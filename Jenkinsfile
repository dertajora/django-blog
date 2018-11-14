pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
                sh 'virtualenv env -p python3.6'
                sh '. env/bin/activate'
                sh 'env/bin/pip install -r requirements.txt'
                sh 'env/bin/python3.6 manage.py test /test'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}