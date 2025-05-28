pipeline {
    agent any

    tools {
        gradle 'Gradle'  // The Gradle installation name in Jenkins Global Tool Config
        jdk 'JDK'        // The JDK installation name in Jenkins Global Tool Config
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/bhavesh-bk/GradleJenkins.git'
            }
        }

        stage('Build') {
            steps {
                // Use gradle wrapper to build (preferred)
                sh './gradlew build'
            }
        }

        stage('Test') {
            steps {
                // Use gradle wrapper to run tests
                sh './gradlew test'
            }
        }

        stage('Run Application') {
            steps {
                // Run the app via gradle wrapper
                sh './gradlew run'
            }
        }
    }

    post {
        success {
            echo 'Build and deployment successful!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
