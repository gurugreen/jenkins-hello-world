pipeline {
  agent any
  stages {
    stage('Echo Version') {
      steps {
        sh 'echo Print Maven Version'
        sh 'mvn --version'
        sh ""echo Sleep-Time ${params.SLEEP_TIME}, Port ${params.APP_PORT}, Branch ${params.BRANCH_NAME}""
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
    stage('Deploy') {
      steps {
        sh 'echo Deploying the application'
        sh """java -jar target/hello-demo-*.jar > /dev/null & """
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
