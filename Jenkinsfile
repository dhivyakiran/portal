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
   
                   def filelist = getChangedFilesList() // List of filenames that have changed

                   def filename = filelist.find{item->item.contains("yml")} //Returns the list of files having the yaml file extension from the filelist ArrayList

                   echo "${filename}" //<filename>.yaml
                    if((filename == "dev.yml" || filename == "int.yml" || filename == "test.yml"))
                       {
                            build job: 'angular-pipeline', parameters: [[$class: 'StringParameterValue', name: 'envname', value: '${filename}']], wait: true    
                        }
                    /*else
                    {
                        currentBuild.result = 'ABORTED'
                        error("Stopping build")
                    }*/

                  }

             }

        }
    }

  }

def getChangedFilesList() {


       changedFiles = []

       for (changeLogSet in currentBuild.changeSets) { 

               for (entry in changeLogSet.getItems()) { // for each commit in the detected changes

                      for (file in entry.getAffectedFiles()) {

                             changedFiles.add(file.getPath()) // add changed file to list

                      }

               }

       }

       return changedFiles


}
