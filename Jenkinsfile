pipeline {
    agent any

        stages('SonarQube Analysis') {
            stage ('scan'){
              environment {
                def scannerHome = tool 'SonarQubeScanner', type 'hudson.plugins.sonar.SonarRunnerInstallation';
                }
              steps {
                withSonarQubeEnv(installationName: 'SonarQubeServer') {
                    echo "sonar connection completed"
                }
              }
          }
    }
}
