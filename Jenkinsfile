pipeline {
  agent any
  tools {
    maven 'm3'
  }
  stages {
    stage('Build') {
      steps {
        sh 'mvn clean install -DskipTests'
        archiveArtifacts artifacts: 'target/hello-demo-*jar'
      }
    }
    stage('Test') {
      steps {
        sh 'mvn test'
        junit 'target/surefire-reports/TEST-com.kodekloud.hello_demo.HelloControllerTests.xml'
      }
    }
    stage('Containerization') {
      steps {
        sh 'echo "Building Docker Image"'
      }
    }
    stage('K8s Deployment') {
      steps {
        sh 'echo "Deploying to Kubernetes"'
      }
    }
  }
}