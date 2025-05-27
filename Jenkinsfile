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
            // Declare pipeline environment variables locally or at stage level
            environment {
                 SAMPLE_ENV = credentials("username/password")
            }
            steps {
               sh 'echo $SAMPLE_ENV'
            }
        }
    }
}
