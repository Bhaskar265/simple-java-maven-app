pipeline {
    agent any

    tools {
        maven 'Maven-3.9.11'  // Name from Jenkins global tool config
        jdk 'Java-21'        // Make sure Jenkins has Java 21 installed
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
                sh 'echo "Contents of target folder:"'
                sh 'ls -l target || echo "No target directory found"'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true, onlyIfSuccessful: true
            }
        }
    }

    post {
        success {
            echo '✅ Build and archive succeeded!'
        }
        failure {
            echo '❌ Build failed. Check Maven logs and target folder.'
        }
    }
}
