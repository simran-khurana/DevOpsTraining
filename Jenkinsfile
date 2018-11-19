	node {
  environment {
    registry = “simrandockerhub/dashboard”
    registryCredential = ‘simrandockerhub’
    dockerImage = ‘’
  }
  agent any
  stages {
    stage(‘Cloning repo’) {
        checkout scm
    }
    stage(‘Building image’) {
     
        script {
          dockerImage = docker.build registry + “:$BUILD_NUMBER”
        }
      
    }
    stage(‘Deploy Image’) {
    
        script {
          docker.withRegistry( ‘’, registryCredential ) {
            dockerImage.push()
          }
        
      }
    }
  }
}
