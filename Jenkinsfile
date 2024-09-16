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
               withSonarQubeEnv(credentialsId: 'sonarqube-cred') {
                sh 'sonar-scanner -Dsonar.projectKey=project_key_2 -Dsonar.sources=src'                
                }
            }
        }

    }
}
