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
          which ansible
          '''
         }
        }
      stage('Deploy'){
          steps{ 
             sh '''
              ansible-playbook -i ansible/deployment/hosts ansible/deployment/my_playbook.yaml --private-key=ansible/mykey
              '''
        } 
      }
    }   
  }
