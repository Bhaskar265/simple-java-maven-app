pipeline {
    agent any

    tools {
        maven 'Maven-3.8.7' // Must match the Maven name in Jenkins Tools
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'git@github.com:Bhaskar265/simple-java-maven-app.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Archive Artifact') {
            steps {
                // Archive the JAR file from target folder
                archiveArtifacts artifacts: '**/*.jar', fingerprint: true
            }
        }
    }
    }
}


