pipeline {
    agent any
    options {
       buildDiscarder(logRotator(numToKeepStr:'3'))
    }

    stages {
      stage ('initialize') {
        sh '''
        git branch
        echo "path=${path}"
        echo | java -version
        echo | git -version
        '''
        ansiblePlaybook credentialsId: 'mykey', inventory: 'deployment/hosts', playbook: 'my_plabook.yaml'
        }
     }
        
  }
