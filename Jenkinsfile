pipeline {
    agent { label 'Worker-1' }

    parameters {
    gitParameter branchFilter: 'origin/(.*)', defaultValue: 'master', name: 'BRANCH', type: 'PT_BRANCH'
  }

    stages {

     stage('Clone repository') {
        steps{
             git branch: "${params.BRANCH}", url: 'git@github.com:dmitrii-saprin/test.git', credentialsId: 'jenkins'
        }
    }

         stage('Check') {
         steps{
          sh "docker ps"
         }
     }



  }

         post {
        always {
            cleanWs()
        }
    }
}