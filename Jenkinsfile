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
					echo mydata.message.test
                  
                }
			}
		}
		stage('Zip the app') {
			steps 
			{
				script{
					zip archive: true, dir: './src', glob: '', zipFile: mydata.zipfile.filename+"_${currentBuild.number}.zip"
                } 
			}
		}
		
		
	}
		post {
    always {
        emailext body: 'A Test EMail', recipientProviders: [[$class: 'DevelopersRecipientProvider'], [$class: 'RequesterRecipientProvider']], subject: 'Test'
    }
}
}
	
	

