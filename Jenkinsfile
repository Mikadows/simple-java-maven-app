pipeline {

    agent any
    def scannerHome = tool 'SonarScanner 4.0';
    
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
                    sh "${scannerHome}/bin/sonar-scanner -Dproject.settings=sonar.properties"
                }
            }
        }
    }
}
