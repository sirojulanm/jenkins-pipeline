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
                echo "Hello Build Processed 1"
                echo "Hello Build Processed 2"
                echo "Hello Build Processed 3"
            }
        }
        stage("Test") { 
            steps {
                echo "Hello Test Processed 1"
                echo "Hello Test Processed 2"
                slepp(5)
                echo "Hello Test Processed 3"
            }
        }
        stage("Deploy") { 
            steps {
                echo "Hello Deploy Processed 1"
                echo "Hello Deploy Processed 2"
                echo "Hello Deploy Processed 3"
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