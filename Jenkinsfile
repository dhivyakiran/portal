pipeline  {   
agent
{
   label "master"
}
stages  
{ 
   stage('Clone sources')  
   {
      steps  
      {
         script 
         {
   
                   def changeLogSets = currentBuild.changeSets
           for (int i = 0; i < changeLogSets.size(); i++) {
           def entries = changeLogSets[i].items
           for (int j = 0; j < entries.length; j++) {
               def entry = entries[j]
               echo "${new Date(entry.timestamp)}: ${entry.msg}"
               def files = new ArrayList(entry.affectedFiles)
               for (int k = 0; k < files.size(); k++) {
                   def file = files[k]
                   echo "all commited files : ${file.path}"
                  def filename = file.path
                 
                def filevalue=filename.split(/\./)
                  echo "split the yml filename: ${filevalue}"
                    if((filename == "dev.yml" || filename == "int.yml" || filename == "qa.yml"))
                       {
                           build job: 'angular-pipeline',  parameters: [[$class: 'StringParameterValue', name: 'envname', value: filevalue[0]]], wait: true    
                        echo "entered success"
                       }
               }
           }
           }
                   
                    }

             }

        }
    }

  }





