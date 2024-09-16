pipeline {
    agent any

    stages {
        stage('Trivy fs scan') {
            steps {
                sh "trivy fs ."
            }
        }

        stage('docker build') {
            steps {
            withDockerRegistry(credentialsId: 'docker-creds', url: 'https://index.docker.io/v1/') {
                sh "docker build -t za357627acc1/adservice"
                }
            }
        }

        stage('docker push') {
            steps {
            withDockerRegistry(credentialsId: 'docker-creds', url: 'https://index.docker.io/v1/') {
                sh "docker push za357627acc1/adservice:latest"
                }
            }
        }

        stage('Trivy fs scan') {
            steps {
                sh "trivy fs ."
            }
        }
    }
}
