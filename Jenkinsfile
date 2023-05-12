pipeline {
    agent 

    environment {
        DOCKERHUB_CREDENTIALS = credentials('jenkins-dockerhub') 
    }

    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t Jenkins_test:latest .'
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'echo $DOCKERHUB_CREDENTIALS_USR | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
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
