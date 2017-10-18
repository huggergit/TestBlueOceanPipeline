pipeline {
  agent any
  stages {
    stage('Confirm Start') {
      steps {
        input(message: 'Please confirm deployment', id: 'ConfirmDeployStart', ok: 'Yes?')
      }
    }
    stage('Banner Updates') {
      steps {
        parallel(
          "Add PC Banner": {
            echo 'Add PC Banner'
            
          },
          "Add BC Banner": {
            echo 'BC Banner'
            
          },
          "Script Parameter": {
            echo 'PolicyCenter Script Parameter Update							 1	http://mislnxp06.cgic.ca:8080/pc/PolicyCenter.do						 2	Login with your employee #						 3	Click \'Administration\'  then \'Script Parameters\' on left menu						 4	Find parameter DocProdPayloadLastPurgeDate in list and Edit.						 5	Change value to 15/10/2015 and Update						NOTE: To confirm, the date for the script parameter is 2 years before the implementation date, ie:  October 15, 2015. 							'
            
          },
          "Pre-war Imports": {
            echo '	Steps to be done only on this Server mislnxp06.cgic.ca 	 	R43 Pre-war Rate Book Load  1	cd /mnt/ProdCluster/deploy/prod/pc/RELEASE43 2	unzip PolicyCenterAdminData.zip 3	cd /mnt/ProdCluster/deploy/prod/pc/RELEASE43/data/ratebooks/auto 4	gunzip -v * 5	cd /mnt/ProdCluster/deploy/prod/pc/RELEASE43/data/ratebooks/commercial 6	gunzip -v * 7	cd /mnt/ProdCluster/deploy/prod/pc/RELEASE43/data/ratebooks/RBP 8	gunzip -v * 9	nohup ~/scripts/policycenter/import_ratebook_lists.sh /mnt/ProdCluster/deploy/prod/pc/RELEASE43/data/ratebooks/Upgrade/R43/R43PreWarRatebooks.lst > /var/log/policycenter/prod/R43PreWarRatebooksImport.log & 10	tail -f /var/log/policycenter/prod/R43PreWarRatebooksImport.log 	 	Unzipping will take 10 minutes or less to complete in total (including gunzip step) 	Import will take less than 30 minutes to complete 	 	 	R43 Pre-war Admin Data Load 11	nohup ~/scripts/policycenter/import_data_lists.sh /mnt/ProdCluster/deploy/prod/pc/RELEASE43/data/main/Upgrade/R43/R43PreWarImport.lst > /var/log/policycenter/prod/R43PreWarImport.log & 12	tail -f /var/log/policycenter/prod/R43PreWarImport.log'
            
          },
          "Manual hold on BC BIRT": {
            echo 'Call OPS at 1-866-203-1986 ask for Job CSBD3410 to be put on manual hold for Sunday morning(Oct. 15th 2017)'
            
          }
        )
      }
    }
    stage('Confirm Prep Work Completed') {
      steps {
        input(message: 'Please confirm Prep Work has completed', ok: 'Confirmed')
      }
    }
    stage('Tivoli Alerts - Disable') {
      steps {
        echo 'On servers mislnxp06.cgic.ca, mislnxp07.cgic.ca, mislnxp08.cgic.ca, mislnxpr013.cgic.ca, mislnxpr014.cgic.ca, and mislnxpr015.cgic.ca'
      }
    }
    stage('Confirm Deployment Start') {
      steps {
        input(message: 'Confirm Ready to Start Deployment', ok: 'Confirm')
      }
    }
    stage('Pre Shutdown tasks') {
      steps {
        echo 'Suspend BC PC Event Messages'
        echo 'Suspend BC PC Event Messages'
      }
    }
    stage('Stop All PC BC App servers') {
      steps {
        parallel(
          "Stop All PC BC App servers": {
            echo 'Stopping PC on MISLNXP06'
            echo 'Stopping PC on MISLNXP07'
            echo 'Stopping PC on MISLNXP08'
            echo 'Stopping PC on MISLNXPR013'
            echo 'Stopping PC on MISLNXPR014'
            echo 'Stopping PC on MISLNXPR015'
            echo 'Stopping BC on MISLNXP06'
            echo 'Stopping BC on MISLNXP07'
            echo 'Stopping BC on MISLNXP08'
            echo 'Stopping BC on MISLNXPR013'
            echo 'Stopping BC on MISLNXPR014'
            echo 'Stopping BC on MISLNXPR015'
            
          },
          "Stopping PC on MISLNXP06": {
            echo 'Stopping PC on MISLNXP06'
            
          },
          "Stopping PC on MISLNXP07": {
            echo 'Stopping PC on MISLNXP07'
            
          },
          "Stopping PC on MISLNXP08": {
            echo 'Stopping PC on MISLNXP08'
            
          },
          "Stopping PC on MISLNXPR013": {
            echo 'Stopping PC on MISLNXPR013'
            
          },
          "Stopping PC on MISLNXPR014": {
            echo 'Stopping PC on MISLNXPR013'
            
          },
          "Stopping PC on MISLNXPR015": {
            echo 'Stopping PC on MISLNXPR015'
            
          },
          "Stopping BC on MISLNXP06": {
            echo 'Stopping BC on MISLNXP06'
            
          },
          "Stopping BC on MISLNXP07": {
            echo 'Stopping BC on MISLNXP07'
            
          },
          "Stopping BC on MISLNXPR013": {
            echo 'Stopping BC on MISLNXPR013'
            
          },
          "Stopping BC on MISLNXPR014": {
            echo 'Stopping BC on MISLNXPR014'
            
          },
          "Stopping BC on MISLNXPR015": {
            echo 'Stopping BC on MISLNXPR015'
            
          }
        )
      }
    }
    stage('PolicyCenter Database scripts') {
      steps {
        parallel(
          "PolicyCenter Database scripts": {
            echo 'PolicyCenter Database scripts'
            
          },
          "Message Broker": {
            echo 'Message Broker'
            
          },
          "Copy Shell Scripts": {
            echo 'Copy Shell Scripts'
            
          },
          "Ratabase": {
            echo 'Ratabase'
            
          }
        )
      }
    }
    stage('War Deployment') {
      steps {
        parallel(
          "PC War": {
            echo 'PC WAR'
            
          },
          "BC WAR": {
            echo 'BC WAR'
            
          }
        )
      }
    }
    stage('Confirm War Deployment') {
      steps {
        input(message: 'Please Confirm WAR Deployments are successful', ok: 'Confirm')
      }
    }
    stage('Post War Updates and Distribute WAR to Cluster') {
      steps {
        parallel(
          "PC Import": {
            echo 'PC Import'
            
          },
          "Update QAS Files": {
            echo 'Update QAS Files'
            
          },
          "PC WAR Distribute": {
            echo 'PC WAR Distribute'
            
          },
          "BC Admin Imports": {
            echo 'BC Admin Imports'
            
          },
          "BC WAR  Distribute": {
            echo 'BC WAR  Distribute'
            
          },
          "Post-war Imports": {
            echo 'Post-war Imports'
            
          }
        )
      }
    }
    stage('Cleanup') {
      steps {
        parallel(
          "Resume PC/BC Event Message": {
            echo 'Resume PC/BC Event Message'
            
          },
          "enable Crontab on p06": {
            echo 'enable Crontab on p06'
            
          }
        )
      }
    }
    stage('PC/BC BIRT WAR deploy') {
      steps {
        echo 'PC/BC BIRT WAR deploy'
      }
    }
  }
}