pipeline {
  agent any
  stages {
    stage('Confirm Start') {
      steps {
          input(message: 'Please confirm deployment', id: 'ConfirmDeployStart', ok: 'Yes?')        
      }
    }    
    stage('Shutdown App Servers') {
      steps {
        parallel(
          "Shutdown Server1": {
            sh 'Shutdown server1'
            
          },
          "Shutdown Server2": {
            sh 'Shutdown Server 2'
            
          },
          "Shutdown server 3": {
            sh 'Shutdown server 3'
            
          },
        )
      }
    }
    stage('Deploy Bar Local') {
      steps {
        sh 'Deploy Bar Locally'
      }
    }
    stage('Wait for Verification') {
      steps {
        input(message: 'Please Confirm Deployment is successfull', id: 'DeploySuccess', ok: 'Yes?')
      }
    }
  }
}
