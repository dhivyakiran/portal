pipeline  {   
agent
{
   label "master"
}
environment
   {
      lastfile=0
   }
stages  
{ 
   stage('Clone sources')  
   {
      steps  
      {
         script 
         {
            def filename
            def changeLogSets = currentBuild.changeSets
           for (int i = 0; i < changeLogSets.size(); i++) {
           def entries = changeLogSets[i].items
           for (int j = 0; j < entries.length; j++) {
               def entry = entries[j]
               def files = new ArrayList(entry.affectedFiles)
               for (int k = 0; k < files.size(); k++) {
                   def file = files[k]
                   echo "${file.path}"
                  filename=file.path
                  
                    if((filename == "dev.yml" || filename == "int.yml" || filename == "qa.yml"))
                       {
                          echo "yml file get success"
                          lastfile=1
                          break
                       }
                  
               }
           }
           }
            def filevalue=filename.split(/\./)
            if(lastfile==1)
            {
               build job: 'angular-pipeline',  parameters: [[$class: 'StringParameterValue', name: 'envname', value: ${filevalue[0]}]], wait: true
            }
         }
      }
   }
}
}
                   /*def filelist = getChangedFilesList() // List of filenames that have changed

                   def filename = filelist.find{item->item.contains("yml")} //Returns the list of files having the yaml file extension from the filelist ArrayList

                   echo "${filename}" //<filename>.yaml
                   def filevalue=filename.split(/\./)
                    if((filename == "dev.yml" || filename == "int.yml" || filename == "qa.yml"))
                       {
                            build job: 'angular-pipeline',  parameters: [[$class: 'StringParameterValue', name: 'envname', value: ${filevalue[0]}]], wait: true    
                        }
                    }

             }

        }
    }

  }*/







