#!groovy
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                slackSend color: "#2196F3", channel: "@carlos.vargas.huaman", message: "Build Started: ${env.JOB_NAME} ${env.BUILD_NUMBER}"
                sh "./gradlew assembleDebug"
            }
        }
        stage('Test') {
            parallel {
                stage('Unit Tests') {
                    steps {
                        slackSend color: "#2196F3", channel: "@carlos.vargas.huaman", message: "Build Started: ${env.JOB_NAME} ${env.BUILD_NUMBER}"
                        sh "./gradlew testDebugUnitTest"
                    }
                }
                stage('UI Tests') {
                    steps {
                        slackSend color: "#2196F3", channel: "@carlos.vargas.huaman", message: "Build Started: ${env.JOB_NAME} ${env.BUILD_NUMBER}"
                        sh './gradlew connectedDebugAndroidTest'
                    }
                }
            }
        }
        stage('Lint') {
            steps {
                slackSend color: "#2196F3", channel: "@carlos.vargas.huaman", message: "Build Started: ${env.JOB_NAME} ${env.BUILD_NUMBER}"
                sh './gradlew lintDebug'
            }
        }
        stage('Deploy') {
            steps {
                slackSend color: "#2196F3", channel: "@carlos.vargas.huaman", message: "Build Started: ${env.JOB_NAME} ${env.BUILD_NUMBER}"
                echo 'Deploying....'
            }
        }
        stage("Tag Code") {
            steps {
                echo 'Tagging code....'
            }
        }
    }
}
