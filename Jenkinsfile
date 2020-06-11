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
            echo "show current path: "
            sh pwd
            ansiblePlaybook credentialsId: 'mykey', inventory: 'deployment/hosts', playbook: 'my_plabook.yaml'
         }
        } 
      }
    }   
  }
