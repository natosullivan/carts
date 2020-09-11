pipeline {
    agent any
    tools {
        maven 'Maven 3.6.3'
    }
    stages {
        stage('Build') {
            steps {
                echo "Building..."
                sh 'mvn compile'
            }
        }
        stage('Test') {
            steps {
                echo "Running tests..."
                sh 'mvn clean test'
            }
        }
        stage('Package') {
            steps {
                echo "Packaging..."
                sh 'mvn package -DskipTests'
                archiveArtifacts artifacts '**/target/*.jar', fingerprint: true
            }
        }
    }
}