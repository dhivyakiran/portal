node 
		{
			config = readYaml file: 'sample.yml'
			setConfigEnvironmentVariables(config)
		}
pipeline {
   agent any
	stages {
		stage('Read YML file') {
			steps 
			{
				setConfigEnvironmentVariables()
			}
		}
	}
}
