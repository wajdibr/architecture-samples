pipeline {
    agent any
    environment {
        JAVA_HOME = '/Library/Java/JavaVirtualMachines/jdk-11.0.x.jdk/Contents/Home'  // Remplacez x par votre version exacte
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
}