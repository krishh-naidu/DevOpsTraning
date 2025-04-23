pipeline {
    agent any

        stage('SonarQube Analysis') {
              environment {
                scannerHome = tool 'SonarQubeScanner';
            }
              steps {
                withSonarQubeEnv(installationName: 'SonarQubeServer') {
                    echo "sonar connection completed"
                }
              }
          }
    }
