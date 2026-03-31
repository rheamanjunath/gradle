pipeline {
    agent any  // Use any available agent

    tools {
        gradle 'gradle'  // Ensure this matches the name configured in Jenkins
        jdk 'jdk'
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/rheamanjunath/gradle.git'
            }
        }

        stage('Build') {
            steps {
                sh 'chmod +x gradlew'
                sh './gradlew build'
                // Run Gradle build
            }
        }

        stage('Test') {
            steps {
                sh './gradlew test'  // Run unit tests
            }
        }

        
        
       
        stage('Run Application') {
            steps {
                // Start the JAR application
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
