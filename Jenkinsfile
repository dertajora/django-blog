pipeline {
    environment {
        registry = "dertajora/django-blog"
        registryCredential = 'docker-hub-dertajora'
        dockerImage = ''
    }

    agent any

    stages {
        stage('Build') {
            steps {
                
                script{
                    dockerImage = docker.build registry + ":$BUILD_NUMBER"
                    docker.withRegistry( '', registryCredential ) {
                        dockerImage.push()
                    }
                }
                
                echo 'Building nieeh..'
            }
        }
        stage('Test') {
            parallel {
                stage('Unit Testing'){
                    steps {
                        sh '''
                        virtualenv venv
                        . venv/bin/activate
                        pip3 install -r requirements.txt
                        python3 manage.py migrate
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
                sh 'whoami'
                script{
                    docker.withRegistry( '', registryCredential ) {
                            latestDocker.pull()
                        }
                }

                docker.withRegistry('', registryCredential) {
                    latestDocker = docker.image("dertajora/django-blog:"+ "$BUILD_NUMBER");
                    latestDocker.pull()
                }
                sh 'bash deploy_staging.sh'
                echo 'Deploying to staging....'
            }
        }
        stage('Production Confirmation') {
            steps {
                script {
                    env.DEPLOYMENT_DECISION = input message: 'Deploy on production?',
                    parameters: [choice(name: 'Confirmation', choices: 'No\nYes', description: 'Choose "Yes" if you want to deploy this build')]
                }
                
            }
        }
        stage('Deploy Production'){
            when {
                environment name: 'DEPLOYMENT_DECISION', value: 'Yes'
            }
            steps {
                echo 'Deploying to production....'
            }
        }
    }
}