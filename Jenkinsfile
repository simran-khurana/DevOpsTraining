pipeline {
agent any
    environment {
    PATH = "C:\\Program Files\\Git\\usr\\bin;C:\\Program Files\\Git\\bin;${env.PATH}"
}
    stages {
        stage('Build') {
            steps {
                sh 'docker build --pull -t liatrio/jenkins-alpine:lts .'
            }
        }
      
    }
}
