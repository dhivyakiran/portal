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
		lastfile='0'
	}
	stages  
	{ 
		stage('Trigger the portal pipeline job')  
		{
			steps  
			{
				script 
				{
					
				    lastfile = sh(returnStdout: true, script: 'git diff-tree --no-commit-id --name-status -r HEAD').trim()
					echo "................."+lastfile
					
					echo "aaaaaaaaaaaaaaaaa"+lastfile.indexOf('qa.yml')
					if (lastfile.indexOf('qa.yml')< 0 && lastfile.indexOf('int.yml')< 0)
					{
						    /*build job: 'portal-pipeline',  parameters: [[$class: 'StringParameterValue', name: 'envname', value: "dev"]], wait: true*/
							echo "................."+lastfile
							
					}
					else{
						echo "check"
						/*build job: 'portal-pipeline',  parameters: [[$class: 'StringParameterValue', name: 'envname', value: "dev"]], wait: true*/
						}
				}
			}
		}
	}
}
     
	 
	 
	 
	 


























