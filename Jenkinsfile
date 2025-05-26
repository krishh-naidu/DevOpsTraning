pipeline {
    agent any
    environment {
        global_env = "this is global environment variable"
    }

    stages {
        stage ("Build") {
            environment {
               local_env = "this is local environment variable"
            }
            steps {
                echo "$global_env"
                echo "${local_env}"
            }
        }
    }
}