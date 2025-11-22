pipeline {
    agent any

    tools {
        maven 'maven3'
    }

    stages {

        stage('Checkout') {
            steps {
                git credentialsId: 'github_pat', 
                    url: 'https://github.com/Massara28/ecommerce.git', 
                    branch: 'main'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean test'
            }
        }

        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'target/*.war', onlyIfSuccessful: true
            }
        }
    }
}
