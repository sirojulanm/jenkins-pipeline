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
                echo "Start Build"
                sh("./mvnw clean compile test-compile")
                echo "Finish Build"
            }
        }
        stage("Test") { 
            steps {
                echo "Start test"
                sh("./mvnw test")
                echo "Finish test"
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