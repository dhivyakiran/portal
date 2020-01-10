pipeline {				
    agent any				
    stages {
         stage ("changeset") {		
            steps {
                script
                {
                   /* def changeLogSets = currentBuild.changeSets
           for (int i = 0; i < changeLogSets.size(); i++) {
           def entries = changeLogSets[i].items
           for (int j = 0; j < entries.length; j++) {
               def entry = entries[j]
                def files = new ArrayList(entry.affectedFiles)
               for (int k = 0; k < files.size(); k++) {
                   def file = files[k]
                   echo "filename: ${file.editType.name} ${file.path}"
       
                
               }
          }
          }*/
             
                def filename = ""
def changeSet = currentBuild.rawBuild.changeSets               
for (int i = 0; i < changeSet.size(); i++) 
{
   def entries = changeSet[i].items;
   for (int i = 0; i < changeSet.size(); i++) 
            {
                       def entries = changeSet[i].items;
                       def entry = entries[0]
                       filename += "${entry.editType.name}"
            } 
 }
                    echo ${filename}
                    
               
                }
            }
        }
         stage ("build") {		
             steps
             {
                  if(filename == "app.yml"){
                   echo "run the job"
                   build job: 'angular-pipeline', wait: true
                  }
             }
             
         }
    }
}
