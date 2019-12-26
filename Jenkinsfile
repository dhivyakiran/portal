node 
{
	git url: 'https://github.com/dhivyakiran/helloworld-angular.git'
	mydatas = readYaml file: "sample.yml"
}
pipeline 
{
	agent
	{
    	label 'master'
    }
   	stages 
	{
		stage('Read YML file from another repository') 
		{
			steps 
			{
				script 
				{
					git url: 'https://github.com/dhivyakiran/angular-yml.git'
					testdatas = readYaml file: "test.yml"
					echo testdatas.test.message
			    }
			}
		}	
		stage('Read YML file from current repository') 
		{
			steps 
			{
				script 
				{
			  	    echo "Build url:${currentBuild.absoluteUrl}"
			    }
			}
		}
	    stage('Download Dependencies')
        {
			when {expression{mydatas.pipeline != "Deploy" }}
			steps 
			{
				//nodejs(nodeJSInstallationName: 'NodeJS')
				//{
					sh 'npm install'
				//}
		    }
        }
	    stage('Zip the app')
	    {
			when {expression{mydatas.pipeline != "Deploy" }}    
			steps 
			{
				script
				{
					zip archive: true, dir: './src', glob: '', zipFile: mydatas.zipfile.filename+"_${currentBuild.number}.zip"
                } 
			}
        }
		stage('upload zipfile to nexus artifact') 
		{
            steps
            {
				nexusArtifactUploader artifacts: [[artifactId: 'HelloWorldApp', classifier: '', file: "HelloWorldApp_${currentBuild.number}.zip", type: 'zip']], credentialsId: 'b540a6d8-00dc-4524-af49-8d99d20d3919', groupId: 'org.sonatype.nexus', nexusUrl: 'localhost:8081', nexusVersion: '3.20.0-04', protocol: 'http', repository: 'helloworld-angular', version: '1.0.0'
            }
        }
	}
	/*post 
	{
		always 
		{
			mail to: 'dhivya.k@cognizant.com',
			subject: "${currentBuild.result} pipeline: ${currentBuild.fullDisplayName}",
			body: "${currentBuild.absoluteUrl} has result ${currentBuild.result}"
	    }
	}*/
}

