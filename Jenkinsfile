	node {
  environment {
    registry = “simrandockerhub/dashboard”
    registryCredential = ‘simrandockerhub’
    dockerImage = ‘’
  }
  agent any
  stages {
    stage(‘Cloning Git’) {
      steps {
      
        checkout scm
      }
    }
    stage(‘Building image’) {
      steps{
        script {
          dockerImage = docker.build registry + “:$BUILD_NUMBER”
        }
      }
    }
    stage(‘Deploy Image’) {
      steps{
        script {
          docker.withRegistry( ‘’, registryCredential ) {
            dockerImage.push()
          }
        }
      }
    }
  }
}