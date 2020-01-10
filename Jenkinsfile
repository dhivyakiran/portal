pipeline {				
    agent any				
    stages {
         stage ("build") {		
            steps {
               build job: 'angular-pipeline', wait: true
            }
        }
    }
}
