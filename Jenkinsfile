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
            steps{
                withSonarQubeEnv('sonarqube') {
                    sh 'java -version'
                    sh 'mvn spnar:sonar -target 1.7'
                }
            }
        }
    }
}
