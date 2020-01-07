node 
{
    git url: 'https://github.com/dhivyakiran/helloworld-angular.git'
    mydatas = readYaml file: "sample.yml"
}
pipeline 
{
agent
{
    label 'master'
    }
    stages 
{
/*stage('Read YML file from another repository') 
{
steps 
{
script 
{
git url: 'https://github.com/dhivyakiran/angular-yml.git'
testdatas = readYaml file: "test.yml"
echo testdatas.test.message
   }
}
}*/ 
stage('Read YML file from current repository') 
{
steps 
{
script 
{
     echo "Build url:${currentBuild.absoluteUrl}"
   }
}
}
/* stage('Display changeset') {
      steps {
        script {
           def changeLogSets = currentBuild.changeSets
           for (int i = 0; i < changeLogSets.size(); i++) {
           def entries = changeLogSets[i].items
           for (int j = 0; j < entries.length; j++) {
               def entry = entries[j]
               echo "${new Date(entry.timestamp)}: ${entry.msg}"
               def files = new ArrayList(entry.affectedFiles)
               for (int k = 0; k < files.size(); k++) {
                   def file = files[k]
                   echo " ${file.editType.name} ${file.path}"
               }
           }
           }
               }
            }
           }*/
        

   stage('Download Dependencies')
        {
when {expression{(mydatas.pipeline != "Deploy")}}
steps 
{
nodejs(nodeJSInstallationName: 'NodeJS')
{
sh 'npm install'
}
   }
        }
  
  stage('Zip the sales app')
   {
    
    steps 
    {
       when {expression{(mydatas.pipeline != "Deploy")||(mydatas.artifact.sales=="sales")}}    
      script
    {
        zip archive: true, dir: mydatas.artifact.sales, zipFile: "salesportal/"+mydatas.artifact.sales+"_${currentBuild.number}.zip"

      } 
    when {expression{(mydatas.pipeline != "Deploy")||(mydatas.artifact.agent=="agent")}}    
      script
    {
        zip archive: true, dir: mydatas.artifact.agent, zipFile: "agentportal/"+mydatas.artifact.agent+"_${currentBuild.number}.zip"

      } 

    when {expression{(mydatas.pipeline != "Deploy")||(mydatas.artifact.members=="members")}}    
      script
    {

        zip archive: true, dir: mydatas.artifact.members, zipFile: "memberportal/"+mydatas.artifact.members+"_${currentBuild.number}.zip"
      } 
}
    
   }   
    /* stage('UnZip the app')
   {
when {expression{(mydatas.pipeline != "Deploy")||(mydatas.artifact == "sales")}}    
steps 
{
script
{
unzip dir: '.', glob: '', zipFile: mydatas.zipfile.filename+"_${currentBuild.number}.zip"
                } 
}
        }*/
}
/*post 
{
always 
{
mail to: 'dhivya.k@cognizant.com',
subject: "${currentBuild.result} pipeline: ${currentBuild.fullDisplayName}",
body: "${currentBuild.absoluteUrl} has result ${currentBuild.result}"
   }
}*/
}
