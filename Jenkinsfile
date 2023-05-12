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

        stage('Push Docker Image') {
            steps {
                script {
                    sh 'echo \$DOCKERHUB_CREDENTIALS_USR | docker login -u \$DOCKERHUB_CREDENTIALS_USR --password-stdin'
                    sh 'docker push Jenkins_test:latest'
                }
            }
        }
    }

    post {
        always {
            script {
                sh 'docker logout'
            }
        }
    }
}
