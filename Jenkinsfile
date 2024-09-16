pipeline {
    agent any

    stages {
        stage('Trivy fs scan') {
            steps {
                sh "trivy fs ."
            }
        }

        stage('Build and SonarQube Analysis') {
            steps {
                script {
                    // Ensure gradlew is executable
                    sh 'chmod +x gradlew'
                    
                    // Run Gradle build and SonarQube analysis
                    sh './gradlew clean build sonarqube'
                }
            }
        }
    }
}
