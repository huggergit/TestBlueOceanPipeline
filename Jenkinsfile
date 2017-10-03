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
            sh 'ssh -n gwadmin@mislnxnp014 "cd /data/csiapp/apacheupgrade/policycenter/test1 && ./tomcat.sh stop"'
            
          },
          "Shutdown Server2": {
            sh 'ssh -n gwadmin@mislnxnp014 "cd /data/csiapp/apacheupgrade/policycenter/test2 && ./tomcat.sh stop"'
            
          },
          "Shutdown server 3": {
            sh 'ssh -n gwadmin@mislnxnp014 "cd /data/csiapp/apacheupgrade/policycenter/test3 && ./tomcat.sh stop"'
            
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