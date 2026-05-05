pipeline {
    agent any

    tools {
        sonarQube 'sonarqube'
    }

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/AmritRaj7461/DevOps.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t my-app .'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('sonarqube') {
                    sh '''
                    sonar-scanner \
                    -Dsonar.projectKey=my-frontend-app \
                    -Dsonar.sources=. \
                    -Dsonar.host.url=http://15.206.92.125:9000 \
                    -Dsonar.login=$SONAR_AUTH_TOKEN
                    '''
                }
            }
        }
    }
}