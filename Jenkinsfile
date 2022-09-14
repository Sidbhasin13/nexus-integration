pipeline {
  agent any
  environment {
    BRANCH = "${BRANCH_NAME}"
    USERNAME = 'admin'
    PASSWORD = '3b6b9f2d-a1de-3518-9d33-74ccc3fddfa0'
//     NEXUS_URL = '::1:8011'
  }
  stages {
    stage('Build') {
      when {
          branch 'main'
      }
      steps{
          sh(script: """
              curl -v -u admin:3b6b9f2d-a1de-3518-9d33-74ccc3fddfa0 -X 'GET' 'http://localhost:8011/service/rest/v1/repositories' -H 'accept: application/json'
            """ 
        )
      }
    }
  }
}
