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
              URL="http://${USERNAME}:${PASSWORD}@${NEXUS_URL}/service/rest/v1/repositories --stderr -"
              abc="curl -X GET ${URL} -H 'Content-Type: application/json' --stderr -"
              echo "abc"
            """ 
        )
      }
    }
  }
}
