pipeline {
  agent any
  tools {
    maven 'm3'
  }
  stages {
    stage('Maven Version') {
      steps {
        sh 'mvn -version'
      }
    }
    stage('Build') {
      steps {
        sh 'mvn clean install -DskipTests'
      }
    }
    stage('Test') {
      steps {
        sh 'mvn test'
      }
    }
  }
}