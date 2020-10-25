pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Building...'
        sh 'mvn compile'
      }
    }

    stage('Test') {
      steps {
        echo 'Running tests...'
        sh 'mvn clean test'
      }
    }

    stage('Package') {
      parallel {
        stage('Package') {
          steps {
            echo 'Packaging...'
            sh 'mvn package -DskipTests'
          }
        }

        stage('error') {
          steps {
            archiveArtifacts 'target/*.jar'
          }
        }

      }
    }

  }
  tools {
    maven 'Maven 3.6.3'
  }
}