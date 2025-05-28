pipeline {
    agent any  // Use any available agent
    def gradleHome = tool name: 'gradle-8.6', type: 'gradle'
withEnv(["PATH+GRADLE=${gradleHome}/bin"]) {
    sh 'gradle build'
}




    tools {
        gradle 'Gradle'  // Ensure this matches the name configured in Jenkins
        jdk 'JDK'
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/bhavesh-bk/GradleJenkins.git'
            }
        }

        stage('Build') {
            steps {
                sh './gradlew build'
  // Run Maven build
            }
        }

       stage('Test') {
           steps {
               sh 'gradle test'  // Run unit tests
           }
        }

              
        stage('Run Application') {
            steps {
                // Start the JAR application
                sh 'gradle run'
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

