pipeline {
    agent any
    environment {
        ANDROID_HOME = '/Users/wajdibenrabah/Library/Android/sdk'
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                sh './gradlew assembleDebug'
            }
        }
        stage('Test') {
            steps {
                sh './gradlew test'
            }
        }
    }
}
