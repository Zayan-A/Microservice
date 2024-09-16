pipeline {
    agent any

    stages {
        stage('Trivy fs scan') {
            steps {
                sh "trivy fs ."
            }
        }

    stage('Sonarqube code quality check') {
            steps {
               withSonarQubeEnv("sonarqube") {
                sh 'sonar-scanner -Dsonar.projectKey=project_key_2 -Dsonar.sources=src'                
                }
            }
        }

    }
}
