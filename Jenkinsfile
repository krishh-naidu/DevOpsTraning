pipeline {
    agent any
        stages('SonarQube Analysis') {
            stage ('scan'){
              environment {
                scannerHome = tool 'SonarQubeScanner';
                }
              steps {
                withSonarQubeEnv(installationName: 'SonarQubeServer') {
                    sh "${scannerHome}/bin/SonarQubeScanner"
                    echo "sonar connection completed"
                }
              }
          }
    }
}
