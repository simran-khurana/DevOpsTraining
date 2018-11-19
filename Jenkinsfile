	node {
  environment {
    registry = "simrandockerhub/dashboard"
    registryCredential = 'simrandockerhub'
    dockerImage = ''
	 PATH = "C:\\Program Files\\Git\\usr\\bin"
  }

  
    stage('Cloning repo') {
        checkout scm
    }
	  stage('Build') {
   
         sh 'npm install'
         sh 'npm run bowerInstall'
      
    }
    stage('Test') {
   
        sh 'npm test'
      
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
