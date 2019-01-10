pipeline {
   agent none
   stages {
      stage('Staging Deployment Setup') {
         agent any
         when {
            branch 'staging'
         }
         steps {
            echo 'Create Release Pack' 
            sh 'tar czvf release.tgz README.md components.yaml'
            
            archiveArtifacts artifacts: 'release.tgz'
            gateProducesArtifact file: 'release.tgz'
         }
      }
      stage('UAT Deployment Setup') {
         when {
            branch 'uat'
         }
         steps {
            echo 'Create Release Pack' 
            gateConsumesArtifact file: 'release.tgz'
         }
      }
      stage('Deploy') {
         steps {
            echo 'Deployment'
         }
      }
   }
}
