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
				zip zipFile: mydata.zipfile.filename.zip, archive: true, dir: ''
			}
		}
		
		stage('upload zipfile to nexus artifact') {
			steps 
			{
				 nexusArtifactUploader artifacts: [[artifactId: 'art-Id', classifier: '', file: "HelloWorldApp" + ".zip",, type: 'zip']], credentialsId: 'nexus-creds', groupId: 'com.group', nexusUrl: 'http://localhost:8081/repository/', nexusVersion: '3.20.0-04', protocol: 'https', repository: 'helloworld-angularapp', version: '1.0.0'
			}
		}
	}
}
