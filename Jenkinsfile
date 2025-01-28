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

    triggers {
        // cron("*/5 * * * *")
        // pollSCM('* * * * *')
    }

    parameters {
        string(name: "NAME", defaultValue: "Guest", description: "what is your name")
        text(name: "DESCRIPTION", defaultValue: "Guest", description: "tell me about you")
        booleanParam(name: "DEPLOY", defaultValue: false, description: "need to deploy")
        choice(name: "SOCIAL_MEDIA", choices: ['instagram','facebook','twitter'], description: "need to deploy")
        password(name: "SECRET", defaultValue: "", description: "Encrypt key")
    }

    options {
        disableConcurrentBuilds()
        timeout(time: 5, unit: 'MINUTES')
    }
    
    stages {

        stage("Preparation") { 
            stages {
                stage("Prepare Java") {
                    steps {
                        echo("Prepare Java")
                    }
                }
                stage("Prepare Maven") {
                    steps {
                        echo("Prepare Maven")
                    }
                }
            }
        }

        stage("Parameter") { 
            steps {
                echo "hello: ${params.NAME}"
                echo "your descrition is: ${params.DESCRIPTION}"
                echo "your social media is: ${params.DEPLOY}"
                echo "need to deploy: ${params.SOCIAL_MEDIA}"
                echo "your secret is: ${params.SECRET}"
            }
        }

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
            input {
                message "can we deploy?"
                ok "yes, of course"
                parameters {
                    choice(name: "env", choices: ['dev','qa','prod'], description: "wich environment?")
                }
            }
            steps {
                echo "Hello Deploy Processed 1"
                echo "Hello Deploy Processed 2"
                echo "Hello Deploy Processed 3"
            }
        }
        stage("Release") { 
            when {
                expression {
                    return params.DEPLOY
                }
            }
            steps {
                echo "Release it..."
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