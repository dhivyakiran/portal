pipeline {				
    agent any
    
    stages {
          stage("build & SonarQube analysis") {
            environment {
        scannerHome = tool 'SonarQubeScanner'
    }
            steps {
        withSonarQubeEnv('sonarqube') {
            sh "${scannerHome}/bin/sonar-scanner"
        }
        timeout(time: 10, unit: 'MINUTES') {
            waitForQualityGate abortPipeline: true
        }
            }
          }      
}
}
