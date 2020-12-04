pipeline {

    agent any

    stages {
    
        stage ('Git clone') {
            steps {
                git 'https://github.com/Mikadows/simple-java-maven-app.git'
            }
        }
        
        stage ('Maven Test') {
            steps {
                // sh "mvn -version"
                sh "mvn test"
                
            }
        }
        
        stage ('Maven build') {
            steps {
                sh "mvn package"
            }
        }
        
        stage('SonarQube analysis') {
            withSonarQubeEnv('sonarqube') { // You can override the credential to be used
                sh 'mvn sonar:sonar'
            }
        }
    }
}
