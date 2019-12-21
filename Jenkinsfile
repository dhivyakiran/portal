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
				script{
                    zip archive: true, dir: '', glob: '', zipFile: 'HelloWorldApp.zip'
                } 
			}
		}
		
		stage('upload zipfile to nexus artifact') {
			steps 
			{
				 nexusArtifactUploader artifacts: [[artifactId: 'nexus-artifact-uploader', classifier: 'debug', file: "HelloWorldApp.zip", type: 'zip']], credentialsId: 'c9670574-50b0-4d13-ae13-92bacbaeea1f', groupId: 'sp.sd', nexusUrl: 'localhost:8081/nexus', nexusVersion: 'nexus3', protocol: 'http', repository: 'helloworld-angularapp', version: '3.20.0-04'
			}
		}
	}
}
