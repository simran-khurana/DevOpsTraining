	node {
  environment {
    registry = "simrandockerhub/dashboard"
    registryCredential = 'simrandockerhub'
    dockerImage = ''
  }

  
    stage('Cloning repo') {
        checkout scm
    }
	  stage('Build') {
       steps {
         sh 'npm install'
         sh 'npm run bowerInstall'
       }
    }
    stage('Test') {
      steps {
        sh 'npm test'
      }
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