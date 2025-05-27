pipeline {
    agent any
    environment {
        global_env = "this is global environment variable"
    }

    stages {
        stage ("Build") {
            environment {
               build_local_env = "this is local environment variable from BUILD STAGE"
            }
            steps {
                echo "$global_env"
                echo "${build_local_env}"
            }
        }
         stage ("Test") {
            environment {
               test_local_env = "this is local environment variable from TEST STAGE"
            }
            steps {
                echo "$global_env"
                echo "${environment.test_local_env}"
            }
        }
    }
}
