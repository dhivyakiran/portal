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
					
					sh "git diff-tree --no-commit-id --name-status -r HEAD>file"
					sh "grep 'qa' file"
					lastfile = sh(returnStdout: true, script: 'cat file').trim()
					echo "................."+lastfile

					if(lastfile=='0')
					{
						//def filevalue=filename.split(/\./)
						echo "Triggered the portal pipeline"
						build job: 'portal-pipeline',  parameters: [[$class: 'StringParameterValue', name: 'envname', value: "dev"]], wait: true
					}
				}
			}
		}
	}
}
     
	 
	 
	 
	 


























