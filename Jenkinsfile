pipeline {
    agent any
        def scannerHome = tool name: 'SonarQubeScanner', type: 'hudson.plugins.sonar.SonarRunnerInstallation';
        stages('SonarQube Analysis') {
            stage ('scan'){
              steps {
                withSonarQubeEnv(installationName: 'SonarQubeServer') {
                    sh "${scannerHome}/bin/sonar-scanner"
                    echo "sonar connection completed"
                }
              }
          }
    }
}
