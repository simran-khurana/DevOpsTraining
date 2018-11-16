pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'docker build --pull -t liatrio/jenkins-alpine:lts .'
            }
        }
      
    }
}
