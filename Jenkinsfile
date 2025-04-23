pipeline {
    agent any

    stages {
        stage ("Image Prune"){
            steps{
                sh "docker image prune -f"
            }
        }
        stage ("Test") {
            steps {
                echo "Testing Docker connection"
                sh "docker images"
            }
        }  
        stage("Push to Docker Registry")
        {
            steps 
            {
            withCredentials([usernamePassword(credentialsId:"dockerHubAccount",
            usernameVariable:"dockerUser",passwordVariable:"dockerPassword")])
            {
                sh "docker login -u $dockerUser -p $dockerPassword"
                echo "docker images are pushed successful"
            }
            }    
        }
        stage('SonarQube Code Analysis') {
            steps {
                dir("${WORKSPACE}"){
                // Run SonarQube analysis for Python
                script {
                    def scannerHome = tool name: 'SonarQubeScanner', type: 'hudson.plugins.sonar.SonarRunnerInstallation'
                    withSonarQubeEnv(credentialsId: 'SonarQubeToken') {
                        sh "${scannerHome}/bin/sonar-scanner"
                        echo "sonarqube connection successful"
                    }
                }
            }
            }
       }
        
        
        
    }
}
