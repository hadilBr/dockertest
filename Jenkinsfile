pipeline {
    agent any

    environment {
        DOCKERHUB_CREDENTIALS = credentials('jenkins-dockerhub') 
    }

    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t Jenkins_test:latest .'
                }
            }
        }

        stage('Login to Docker Hub') {
            steps {
                script {
                    sh 'echo $DOCKERHUB_CREDENTIALS_USR | docker login -u OCKERHUB_CREDENTIALS_USR --password-stdin'
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker push Jenkins_test:latest'
            }
        }
    }

    post {
        always {
            sh 'docker logout'
        }
    }
}
