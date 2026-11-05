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
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
    }
}
