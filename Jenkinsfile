pipeline {
    agent any 
    environment {
    DOCKERHUB_CREDENTIALS = credentials('karim-dockerhub')
    }
    stages { 

        stage('Build docker image') {
            steps {  
                sh 'docker build -t karimsahebettaba/flask:$BUILD_NUMBER .'
            }
        }
        stage('login to dockerhub') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('push image') {
            steps{
                sh 'docker push karimsahebettaba/flask:$BUILD_NUMBER'
            }
        }
}
post {
        always {
            sh 'docker logout'
        }
    }
}
