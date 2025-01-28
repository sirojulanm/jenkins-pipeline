pipeline {
    // agent {
    //     node {
    //         label "linux && java17"
    //     }
    // }
    agent any

    environment {
        AUTHOR = "Anam"
        EMAIL = "anam@gmail.com"
        APP = credentials("anam_rahasia")
    }
    
    stages {
        stage("Prepare") { 
            steps {
                echo "author: ${AUTHOR}"
                echo "email: ${EMAIL}"
                echo "Start test: ${env.JOB_NAME}"
                echo "Start build: ${env.BUILD_NUMBER}"
                echo "branch name: ${env.BRANCH_NAME}"
                echo "app user: ${APP_USR}"
                echo "app password: ${APP_PSW}"
                sh 'echo "App Password: ${APP_PSW}" > "rahasia.txt"'
            }
        }
        stage("Build") { 
            steps {
                script {
                    def data = [
                        "firstName": "anam",
                        "lastName": "anam 2"
                    ]
                    writeJSON(file: "data.json", json: data)
                }
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