pipeline {
  agent any
  environment {
    BRANCH = "${BRANCH_NAME}"
    USERNAME = 'admin'
    PASSWORD = 'admin'
    NEXUS_URL = 'localhost:8011'
  }
  stages {
    stage('Build') {
      when {
          branch 'main'
      }
      steps{
          sh(script: """
              curl -X GET http://${USERNAME}:${PASSWORD}@${NEXUS_URL}/service/rest/v1/repositories -H 'Content-Type: application/json' 
            """ 
        )
      }
    }
  }
}
