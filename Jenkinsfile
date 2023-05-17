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
                bat 'docker build -t hadilbr/dockertest:latest .'
                bat 'docker login -u hadilbr -p kimseokjin123  docker.io '
                bat 'docker push hadilbr/dockertest:latest'
            }
        }

    }

    post {
        always {
            bat 'docker logout'
        }
    }
}
