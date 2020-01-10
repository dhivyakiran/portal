pipeline {				
    agent any
    environment {
      lastfile = 0
    }
    stages 
    {
      stage ("changeset") 
      {		
         steps 
         {
           script 
           {
             def changeLogSets = currentBuild.changeSets
             for (int i = 0; i < changeLogSets.size(); i++) 
             {
                def entries = changeLogSets[i].items
                for (int j = 0; j < entries.length; j++) 
                {
                    def entry = entries[j]
                    def files = new ArrayList(entry.affectedFiles)
                    for (int k = 0; k < files.size(); k++) 
                    {
                        def file = files[k]
                        echo "${file.path}"
                        filename = file.path
                        echo "filename: ${filename}"
                            if(filename == "Jenkinsfile")
                            {
                                echo "inside if"
                                lastfile=1   
                                break
                            }
                    }
                }
             }
          } 
       }
    }
    stage ("build aangular pipeline") {		
      steps
      {
         script
         {
            if(lastfile == 1)
            {
             build job: 'angular-pipeline', wait: true    
            }
          }
        }
    }
}
}
