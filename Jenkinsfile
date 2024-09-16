pipeline {
    agent any

    environment{
        SCANNER_HOME= tool 'sonarqube'
    }

    stages {
        stage('Trivy fs scan') {
            steps {
                sh "trivy fs ."
            }
        }

    stage('Sonarqube code quality check') {
            steps {
               withSonarQubeEnv("sonarqube") {
                sh "$SCANNER_HOME/bin/sonar-scanner -Dsonar.projectName=project-2 -Dsonar.projectKey=multibranch"             
                }
            }
        }

    }
}
