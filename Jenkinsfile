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
                def scannerHome = tool 'SonarScanner 4.0'
                withSonarQubeEnv('sonarqube') {
                    sh "${scannerHome}/bin/sonar-scanner -Dproject.settings=sonar.properties"
                }
            }
        }
    }
}
