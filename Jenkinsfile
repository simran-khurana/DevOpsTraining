	node {
  environment {
    registry = "simrandockerhub/dashboard"
    registryCredential = 'simrandockerhub'
    dockerImage = ''
  }
 
 
    stage('Cloning repo') {
        checkout scm
    }
    stage('Building image') {
     
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      
    }
    stage('Deploy Image') {
    
        script {
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
          }
        
      }
    
  }
}
