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
            parallel {
                stage('Unit Testing'){
                    steps {
                        sh '''
                        . venv/bin/activate
                        python3 manage.py test test/
                        deactivate
                        '''
                        echo 'Testing nieeh..'
                    }
                }
                stage('Dummy 1 Testing'){
                    steps {
                        echo 'Dummy 1 testing....'
                    }
                }
                stage('Dummy 2 Testing'){
                    steps {
                        echo 'Dummy 2 testing....'
                    }
                }
            }
        }
        stage('Deploy Staging') {
            steps {
                echo 'Deploying to staging....'
            }
        }
        stage('Deploy Production') {
            script {
                env.DEPLOYMENT_DECISION = input message: 'Deploy on production?',
                parameters: [choice(name: 'Confirmation', choices: 'No\nYes', description: 'Choose "Yes" if you want to deploy this build')]
            }
            when {
                environment name: 'DEPLOYMENT_DECISION', value: 'yes'
            }
            steps {
                echo 'Deploying to production....'
            }
        }
    }
}