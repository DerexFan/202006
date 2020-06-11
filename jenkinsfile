pipeline {
    agent any
    options {
       buildDiscarder(logRotator(numToKeepStr:'5'))
    }

    stages {
      stage ('initialize') {
        sh '''
        echo "path=${path}"
        echo | java -version
        echo | git -version
        ansiblePlaybook credentialsId: 'mykey', inventory: 'deployment/hosts', playbook: 'my_plabook.yaml'
        }
     }
        
  }
