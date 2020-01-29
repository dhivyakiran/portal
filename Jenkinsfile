node 
{
   deleteDir()
   git branch: 'development', url: 'https://github.com/dhivyakiran/pipelineportal.git'
   mydatas = readYaml file: "pipeline.yml"
}
pipeline  
{   
	agent
	{
		label "${mydatas.agentname}"
	}
	environment
	{
		lastfile=0
	}
	stages  
	{ 
		stage('Trigger the portal pipeline job')  
		{
			steps  
			{
				script 
				{
					def filename
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
								filename=file.path
								if((filename == "int.yml" || filename == "qa.yml" || filename == "uat.yml" || filename == "prod.yml"))
								{
									lastfile=1
									break
								}
								
							}
						}
					}
					echo "HELLO : ${lastfile}"
					if(lastfile==0)
					{
						//def filevalue=filename.split(/\./)
						//echo "hai:${filevalue}"
						echo "Triggered the portal pipeline"
						build job: 'portal-pipeline',  parameters: [[$class: 'StringParameterValue', name: 'envname', value: "dev"]], wait: true
					}
				}
			}
		}
	}
}
                






















