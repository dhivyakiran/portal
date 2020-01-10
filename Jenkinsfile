pipeline {				
    agent any				
    stages {
         stage ("build") {		
            steps {
                when { changeset "app.yml" }
                build 'angular-pipeline'	
            }
        }
    }
}
