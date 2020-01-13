pipeline {				
    agent any
    
    stages {
          stage("build & SonarQube analysis") {
            agent any
            steps {
                script {
             scannerHome = tool 'SonarQubeScanner';
        }
              withSonarQubeEnv('My SonarQube Server') {
                sh "${scannerHome}/bin/sonar-scanner.bat"
              }
            }
          }      
}
}
