node {
     mydata = readYaml file: "sample.yml"
}
pipeline {
   agent any
	
	stages {
		stage('Read YML file') {
			steps 
			{
				script {
					echo "${currentBuild.number}"
                  
                }
			}
		}
		stage('Zip the app') {
			steps 
			{
				script{
					zip archive: true, dir: '', glob: '', zipFile: {mydata.zipfile.filename}${currentBuild.number}.zip
                } 
			}
		}
		
		stage('upload zipfile to nexus artifact') {
			steps 
			{
				nexusArtifactUploader artifacts: [[artifactId: 'HelloWorldApp', classifier: '', file: "HelloWorldApp.zip", type: 'zip']], credentialsId: 'b540a6d8-00dc-4524-af49-8d99d20d3919', groupId: 'sp.sd', nexusUrl: 'localhost:8081', nexusVersion: '3.20.0-04', protocol: 'http', repository: 'helloworld-angularapp', version: '1.0.0'
			}
		}
	}
}
