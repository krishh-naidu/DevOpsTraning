pipeline {
    agent any
    // Declare pipeline environment variables globally
    environment {
        global_env = "this is global environment variable"
    }

    stages {
        stage ("Build") {
            // Declare pipeline environment variables locally or at stage level
            environment {
               build_local_env = "this is local environment variable from BUILD STAGE"
            }
            steps {
                echo "$global_env"
                echo "${build_local_env}"
            }
        }
        stage ("Test") {
            // Declare pipeline environment variables locally or at stage level
            environment {
               test_local_env = "this is local environment variable from TEST STAGE"
            }
            steps {
                echo "$global_env"
                echo "${env.test_local_env}"
            }
        }
        stage ("Release") {
            // testing credential helper method with secret text
            environment {
                secret_text_example = credentials("rama_secret_text")
                username_password_example = credentials ("rama_username_password") 
            }
            steps {
                sh 'echo $secret_text_example'
                sh 'echo password is $username_password_example_PSW'
                sh 'echo the username is $username_password_example_USR'
                
            }
        }
    }
}
