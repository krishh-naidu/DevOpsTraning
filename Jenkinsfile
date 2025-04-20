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
        
        stage("Push to Docker Registry"){
            steps {
            withCredentials([usernamePassword(credentialsId:"dockerHubAccount",
            usernameVariable:'dockerUser',passwordVariable:'dockerPassword')]){
                sh ('docker login -u ${dockerUser} -p ${dockerPassword}')
                echo "docker login successful"
                sh 'docker tag streamlit:latest ramakrishnadevarakonda/devopstraning:latest'
                sh 'docker push ramakrishnadevarakonda/devopstraning:latest'
            }
            
        }    
            
        }
    }
}
