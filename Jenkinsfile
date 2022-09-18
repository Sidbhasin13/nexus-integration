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
              abc="curl -s -o response.txt -w "%{http_code}" -X GET http://${USERNAME}:${PASSWORD}@${NEXUS_URL}/service/rest/v1/repositories -H 'Content-Type: application/json' --stderr -"
              if [ $abc != "200" ]; then
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
