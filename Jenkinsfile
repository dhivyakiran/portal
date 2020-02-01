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
		stage('Triggering pipeline')  
		{
			steps  
			{
				script 
				{
					
				    lastfile = sh(returnStdout: true, script: 'git diff-tree --no-commit-id --name-status -r HEAD').trim()
					if (lastfile.indexOf('qa.yml')< 0 && lastfile.indexOf('int.yml')< 0 && lastfile.indexOf('uat.yml')< 0 && lastfile.indexOf('prod.yml')< 0)
					{
						    echo "Triggered................."
							build job: 'portal-pipeline',  parameters: [[$class: 'StringParameterValue', name: 'envname', value: "dev"]], wait: true
							
							
							
					}
					
				}
			}
		}
	}
}
     
	 
	 
	 
	 


























