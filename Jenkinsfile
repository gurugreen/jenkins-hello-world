pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "M399"
    }

    stages {
        stage('Echo Version'){
            steps{
                sh 'echo Print Maven Version'
                sh 'mvn --version'
            }
        }
        stage('Build'){
            steps{
                // git branch: 'main', changelog: false, poll: false, url: 'https://github.com/gurugreen/jenkins-hello-world.git'
                sh 'mvn clean package -DskipTests=true'
            }
        }
        stage('Test'){
            steps{
                sh 'mvn test'
            }
            
        }
            
        }
}
    

