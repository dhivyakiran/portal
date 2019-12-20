node {
     mydata = readYaml file: "sample.yml"
}
pipeline {
   agent any
	
	stages {
		stage('Read YML file') {
			steps 
			{
				echo mydata.message.test
			}
		}
		stage('Npm install') {
			steps 
			{
				sh 'npm config ls'
			}
		}
		
	}
}
