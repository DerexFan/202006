pipeline {
    agent any
    options {
       buildDiscarder(logRotator(numToKeepStr:'3'))
    }

    stages {
      stage ('initialize') {
        steps{
          sh '''
          git branch
          echo "path=${path}"
          echo | java -version
          echo | git --version
          '''
         }
        }
      stage('Deploy'){
        steps{
          dir('ansible') {
            ansiblePlaybook credentialsId: 'mykey', inventory: 'deployment/hosts', playbook: '/deployment/my_playbook.yaml'
         }
        } 
      }
    }   
  }
