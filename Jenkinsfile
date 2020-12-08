pipeline {

    agent any

    stages {
    
        stage ('Git clone') {
            steps {
                git(
                    url: "https://github.com/Mikadows/simple-java-maven-app.git",
                    branch: "${BRANCHE}"
                )
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
                    sh "/sonar-scanner/bin/sonar-scanner -Dproject.settings=sonar.properties"
                }
            }
        }
    }
}
