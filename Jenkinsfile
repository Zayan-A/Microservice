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
                    // Run Gradle build and SonarQube analysis
                    sh './gradlew clean build sonarqube'
                }
            }
        }
    }
}
