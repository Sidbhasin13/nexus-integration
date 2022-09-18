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
              http_response="curl -X GET -s -o response.txt -w "%{http_code}" http://${USERNAME}:${PASSWORD}@${NEXUS_URL}/service/rest/v1/repositories -H 'Content-Type: application/json' --stderr -"
              if [ $http_response != "200" ]; then
                  # handle error
              else
                  echo "Server returned:"
                  cat response.txt    
              fi
            """ 
        )
      }
    }
  }
}
