pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
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
/opt/sonar-scanner/bin/sonar-scanner \
-Dsonar.projectKey=my-frontend-app \
-Dsonar.sources=. \
-Dsonar.login=$SONAR_AUTH_TOKEN
'''
                }
            }
        }
    }
}