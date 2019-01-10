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
            
            // archiveArtifacts artifacts: 'release.tgz'
            gateProducesArtifact file: 'components.yaml'
         }
      }
      stage('UAT Deployment Setup') {
         agent any
         when {
            branch 'uat'
         }
         steps {
            echo 'Create Release Pack' 
            gateConsumesArtifact file: 'components.yaml'
         }
      }
      stage('Deploy') {
         agent any
         steps {
            echo 'Deployment'
         }
      }
   }
}
