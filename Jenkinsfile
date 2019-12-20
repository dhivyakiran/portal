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
		stage('Zip the app') {
			steps 
			{
				sh 'ls -ltr'
			}
		}
	}
}
