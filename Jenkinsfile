pipeline {				
    agent any				
    stages {
         stage ("build") {		
            steps {
                script
                {
                     def changeLogSets = currentBuild.changeSets
           //for (int i = 0; i < changeLogSets.size(); i++) {
           //def entries = changeLogSets[i].items
           //for (int j = 0; j < entries.length; j++) {
               //def entry = entries[j]
               def files = changeLogSets.affectedFiles
               //for (int k = 0; k < files.size(); k++) {
                   //def file = files[k]
                   echo "filename: ${files.editType.name}"
                  // if(){
                   
                   //build job: 'angular-pipeline', wait: true
                  // }
              // }
          // }
          // }
               
                }
            }
        }
    }
}
