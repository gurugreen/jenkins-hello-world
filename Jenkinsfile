pipeline {
  agent any
  stages {
    stage('Echo Version') {
      steps {
        sh 'echo Print Maven Version'
        sh 'mvn --version'
      }
    }

    stage('Build') {
      steps {
        sh 'mvn clean package -DskipTests=true'
        archiveArtifacts 'target/hello-demo-*.jar'
      }
    }

    stage('Test') {
      steps {
        sh 'mvn test'
        junit(testResults: 'target/surefire-reports/TEST-*.xml', keepProperties: true, keepTestNames: true)
      }
    }
    stage('container') {
        steps {
            sh 'echo Docker Build Image'
            sh 'echo Docker Tag Image'
            sh 'echo Docker Push Image'
        }
    }
    stage('kubernetes') {
        steps {
            sh 'echo Deploy to kuberenetes using ArgoCD'
        }
    }    
    stage('Integration Test') {
      steps {
        sh 'sleep 5s'
        sh 'curl -s http://localhost:6767/hello'
      }
    }

  }
  tools {
    maven 'M399'
  }
}
