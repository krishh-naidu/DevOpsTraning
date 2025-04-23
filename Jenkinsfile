pipeline {
    agent any

    stages {
        stage('Git Checkout') {
            steps {
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/krishh-naidu/DevOpsTraning.git']])
                echo 'Git Checkout Completed'
            }
        }

        stage('SonarQube Analysis') {
              environment {
                scannerHome = tool 'SonarQubeScanner';
            }
              steps {
                withSonarQubeEnv(installationName: 'SonarQubeServer') {
                  sh "${scannerHome}/bin/sonar-scanner"
                }
              }
          }
    }
}
