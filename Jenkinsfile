pipeline {
    agent any
    // Declare pipeline environment variables globally
    environment {
        global_env = "this is global environment variable"
    }
    // defining parameters  directive
    parameters {
        booleanParam (name: "TEST_BOOLEAN", defaultValue: true, description: "it represents true or false value")
        string (name: "TEST_STRING", defaultValue: "enter single line value here", trim: true, description: "it allows only single line")
        text (name: "TEST_TEXT", defaultValue: "enter multi line value here", description: "it allows multi lines")
        password (name: "TEST_PASSWD", defaultValue: "secret", description: "enter your password here")
        choice (name: "TEST_CHOICE", choices: ["production", "staging", "development"], description: "it allows multi choices")
    }
        

    stages {
        stage ("Build") {
            when{
                //equals(actual: currentBuild.number, expected: 1)
                branch  ".*Jenkins.*"
            }
            // Declare pipeline environment variables locally or at stage level
            environment {
               build_local_env = "this is local environment variable from BUILD STAGE"
            }
            steps {
                echo "$global_env"
                echo "${build_local_env}"
                // we can disolay parameter values using params helper method
                echo "${params.TEST_BOOLEAN}"
                echo "$params.TEST_STRING"
                echo "${params.TEST_TEXT}"
                echo "$params.TEST_PASSWD"
                echo "$params.TEST_CHOICE"
            }
            post{
                always {
                    echo "This block always runs after this stage."
                }
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
    // setting up post actions directive for each status after stages sectuin
    post {
        always {
            echo "This block always runs."
        }
        changed {
            echo "This block runs when the current status is different than the previous one."
        }
        fixed {
            echo "This block runs when the current status is success and the previous one was failed or unstable."
        }
        regression {
            echo "This block runs when the current status is anything except success but the previous one was successful."
        }
        unstable {
            echo "This block runs if the current status is marked unstable."
        }
        aborted {
            echo "This block runs when the build process is aborted."
        }
        failure {
            echo "This block runs when the build is failed."
        }
        success {
            echo "This block runs when the build is succeeded."
        }
        unsuccessful {
            echo "This block runs when the current status is anything except success."
        }
        cleanup {
            echo "This block always runs after other conditions are evaluated."
        }
    }
}
