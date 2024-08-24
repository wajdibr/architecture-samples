pipeline {
    agent any
    tools {
        jdk 'JDK11'  // ou 'JDK17' si vous préférez Java 17
    }
    environment {
        JAVA_HOME = tool 'JDK11'  // ou 'JDK17'
        PATH = "${env.JAVA_HOME}/bin:${env.PATH}"
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
