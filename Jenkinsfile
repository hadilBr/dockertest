pipeline {
    agent any
    
    stages {
        stage('gitclone') {
            steps {
                git url: 'https://github.com/hadilBr/dockertest.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                script {
                    withCredentials([usernamePassword(credentialsId: 'docker-credentials', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                        bat 'docker build -t hadilbr/dockertest:latest .'
                        bat "docker login -u ${DOCKER_USERNAME} -p ${DOCKER_PASSWORD} docker.io"
                        bat 'docker push hadilbr/dockertest:latest'
                    }
                }
            }
        }
    }

    post {
        always {
            bat 'docker logout'
        }
    }
}
