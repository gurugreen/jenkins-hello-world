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
        archiveArtifacts artifacts: 'target/hello-demo-*jar'
      }
    }
    stage('Test') {
      steps {
        sh 'mvn test'
        junit 'target/surefire-reports/TEST-com.kodekloud.hello_demo.HelloControllerTests.xml'
      }
    }
    stage('Local Deploy') {
      steps {
        sh 'nohup java -jar target/hello-demo-0.0.1-SNAPSHOT.jar &'
      }
    }
    stage('Integration Testing') {
      steps {
        sh "sleep ${params.SLEEP_TIME}"
        sh "curl -s http://localhost:${params.APP_PORT}/hello"
      }
    }
  }
}