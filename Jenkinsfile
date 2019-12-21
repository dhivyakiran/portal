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
				 nexusArtifactUploader artifacts: [[artifactId: 'nexus-artifact-uploader', classifier: '', file: "HelloWorldApp.zip", type: 'zip']], credentialsId: 'e7facf13-faec-30ee-a3a3-7591be16370c', groupId: 'sp.sd', nexusUrl: 'http://localhost:8081/repository', nexusVersion: 'nexus3', protocol: 'http', repository: 'helloworld-angularapp', version: '3.20.0-04'
			}
		}
	}
}
