pipeline {
  agent any
  environment {
    BRANCH = "${BRANCH_NAME}"
    USERNAME = 'admin'
    PASSWORD = 'admin'
//     NEXUS_URL = '::1:8011'
  }
  stages {
    stage('Build') {
      when {
          branch 'main'
      }
      steps{
          sh(script: """
              curl -v -u admin:admin -X GET http://localhost:8011/service/rest/v1/repositories -H 'Content-Type: application/json'
            """ 
        )
      }
    }
  }
}
