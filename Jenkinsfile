pipeline {
    // agent {
    //     node {
    //         label "linux && java17"
    //     }
    // }
    agent any
    stages {
        stage("Build") { 
            steps {
                echo "Hello Build Processed"
            }
        }
        stage("Test") { 
            steps {
                echo "Hello Test Processed"
            }
        }
        stage("Deploy") { 
            steps {
                echo "Hello Deploy Processed"
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