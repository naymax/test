pipeline {
    agent { label 'Worker-1' }

    parameters {
    gitParameter branchFilter: 'origin/(.*)', defaultValue: 'master', name: 'BRANCH', type: 'PT_BRANCH'
  }

    stages {

     stage('Clone repository') {
        steps{
             git branch: "${params.BRANCH}", url: 'https://github.com/dmitrii-saprin/test.git', credentialsId: 'jenkins'
        }
    }

         stage('Build') {
         steps{
          sh "docker build -t s0fitlabs/pls-dev:0.1-ubuntu20.04-amd64 -f ubuntu20.04-amd64 ."
         }
     }



  }

         post {
        always {
            cleanWs()
        }
    }
}