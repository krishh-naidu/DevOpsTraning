pipeline {
    agent any

        stage('SonarQube Analysis') {
              environment {
                scannerHome = tool 'SonarQubeScanner';
            }
              steps {
                withSonarQubeEnv(installationName: 'SonarQubeServer') {
                  # sh "${scannerHome}/bin/sonar-scanner"
                    echo "sonar connection completed"
                }
              }
          }
    }
}
