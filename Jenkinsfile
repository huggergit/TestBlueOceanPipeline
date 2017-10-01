pipeline {
  agent any
  stages {
    stage('Shutdown Server1') {
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
          "Confirm Start": {
            input(message: 'Please confirm deployment', id: 'ConfirmDeployStart', ok: 'Yes?')
            
          }
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