pipeline {
    agent any
    tools {
        jdk 'JDK11'
    }
    environment {
        JAVA_HOME = tool 'JDK11'
        PATH = "${env.JAVA_HOME}/bin:${env.PATH}"
        ANDROID_HOME = '/Users/wajdibenrabah/Library/Android/sdk'
    }
    stages {
        stage('Environment Check') {
            steps {
                sh 'java -version'
                sh './gradlew --version'
                sh 'echo $JAVA_HOME'
                sh 'echo $ANDROID_HOME'
            }
        }
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Clean') {
            steps {
                sh './gradlew clean'
            }
        }
        stage('Build') {
            steps {
                sh './gradlew assembleDebug --stacktrace'
            }
        }
        stage('Test') {
            steps {
                sh './gradlew test --stacktrace'
            }
        }
    }
    post {
        always {
            archiveArtifacts artifacts: 'app/build/outputs/apk/debug/*.apk', fingerprint: true
            junit '**/TEST-*.xml'
        }
    }
}