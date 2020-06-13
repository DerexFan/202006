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
        #steps{
        #  dir('ansible') {
        #      ansiblePlaybook credentialsId: '53d036d3-9256-4c3b-98db-4b77af8260ba', inventory: 'deployment/hosts', playbook: 'deployment/my_playbook.yaml'
        #    
        # }
            }
          steps{ 
             sh '''
              ansible-playbook -i ansible/deployment/hosts ansible/deployment/my_playbook.yaml --private-key=ansible/mykey
              '''
        } 
      }
    }   
  }
