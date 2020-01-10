pipeline {				
    agent any	
    environment {
        lastfile = 'default'
    }
    stages {
         stage ("changeset") {		
            steps {
               script {
           def changeLogSets = currentBuild.changeSets
           env.trigger
           for (int i = 0; i < changeLogSets.size(); i++) {
           def entries = changeLogSets[i].items
           for (int j = 0; j < entries.length; j++) {
               def entry = entries[j]
               def files = new ArrayList(entry.affectedFiles)
               for (int k = 0; k < files.size(); k++) {
                   def file = files[k]
                   echo " ${file.editType.name} ${file.path}"
                   filename = file.editType.name
                   if(filename == "Jenkinsfile"){
                   lastfile="true";    
                   break; 
                   }
               }
              
           }
            }
                if(lastfile=="true"){
                  echo "hi"
                      
                 }  
               
               } 
                 
            }
        }
          /*stage ("build") {		
               when {expression{(env.trigger=="true")}}
              steps{
                  
                 //script{
                  //if(env.trigger==true){
                  echo "hi"
                      
                 // }
                  //}
              }
          }*/
    }
}
