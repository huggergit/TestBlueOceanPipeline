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
            
          }
        )
      }
    }
  }
}