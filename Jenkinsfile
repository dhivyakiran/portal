pipeline {				
    agent any
    stages {
          stage("build & SonarQube analysis") {
          /*environment 
          {
              scannerHome = tool 'SonarQubeScanner'
          }*/
          steps {
          /* withSonarQubeEnv('sonarqube') 
          {
            bat "${scannerHome}/bin/sonar-scanner"
          }
          timeout(time: 10, unit: 'MINUTES') 
          {
            waitForQualityGate abortPipeline: true
          }*/
          bat "sonar-scanner -X"
          }
       }      
    }
}
