pipeline {
    // agent {
    //     node {
    //         label "linux && java17"
    //     }
    // }
    agent any
    stages {
        stage("Hello anam") { 
            steps {
                echo "Hello pipeline build by anam"
            }
        }
    }

    post {
        always {
            echo "i will always say hello if processed"
        }
        success {
            echo "this process success"
        }
        failure {
            echo "oh no, failure"
        }
        cleanup {
            echo "dont care success of  error"
        }
    }
}