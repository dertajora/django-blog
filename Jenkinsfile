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
                . venv/bin/activate
                python3 manage.py test test/
                deactivate
                '''
                echo 'Testing nieeh..'
            }
        }
        stage('Deploy Staging') {
            steps {
                script {
                env.DEPLOYMENT_DECISION = input message: 'Deploy on production?',
                    parameters: [choice(name: 'Confirmation', choices: 'No\nYes', description: 'Choose "Yes" if you want to deploy this build')]
                }
                echo 'Deploying....'
            }
        }
        stage('Deploy Production') {
            when {
                environment name: 'DEPLOYMENT_DECISION', value: 'yes'
            }
            steps {
                echo 'Deploying....'
            }
        }
    }
}