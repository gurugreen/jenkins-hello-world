pipeline {
    agent any

    tools {
        maven 'm3'
    }

    stages {
        stage('Echo Maven Version') {
            steps {
              sh '''
                echo "Maven Version"
                mvn -version
              '''             
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean install -DskipTests'
                archiveArtifacts artifacts: 'target/hello-demo-*.jar', followSymlinks: false
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
                junit 'target/surefire-reports/TEST-com.kodekloud.hello_demo.HelloControllerTests.xml'
            }
        }
    }
}
