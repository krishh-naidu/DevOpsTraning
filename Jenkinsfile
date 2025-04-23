pipeline {
    agent any
        stages('SonarQube Analysis') {
            stage ('scan'){
              environment {
                scannerHome = tool 'SonarQubeScanner';
                }
              steps {
                withSonarQubeEnv(credentialsId: SonarQubeToken', installationName: 'SonarQubeServer') {
                    sh "${scannerHome}/bin/sonar-scanner"
                    echo "sonar connection completed"
                }
              }
          }
    }
}
