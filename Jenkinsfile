pipeline {
    agent any
        stages('SonarQube Analysis') {
            stage ('scan'){
              environment {
                scannerHome = tool 'SonarQubeScanner';
                }
              steps {
                withSonarQubeEnv(installationName: 'SonarQubeServer') {
                    sh "${scannerHome}/bin/"
                    echo "sonar connection completed"
                }
              }
          }
    }
}
