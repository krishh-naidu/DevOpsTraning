pipeline {
    agent any
        def scannerHome = tool name: 'SonarQubeScanner', type: 'hudson.plugins.sonar.SonarRunnerInstallation';
        stages('SonarQube Analysis') {
            stage ('scan'){
              environment {
                
                }
              steps {
                withSonarQubeEnv(installationName: 'SonarQubeServer') {
                    echo "sonar connection completed"
                }
              }
          }
    }
}
