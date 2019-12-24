node {
     mydatas = readYaml file: "sample.yml"
}

pipeline {
	agent
                {
                    node
                            {
                                label "mydatas.agent.name"
                            }
                }

     	stages 
	{
	   stage('Read YML file') {
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
                   steps {
			   nodejs(nodeJSInstallationName: 'NodeJS'){
    			sh 'npm install'
}
		      }
                }

	    stage('Zip the app')
	    {
		steps 
		{
	            script
		      {
			zip archive: true, dir: './src', glob: '', zipFile: mydatas.zipfile.name+"_${currentBuild.number}.zip"
                      } 
		}
             }
		
	  }
	post {
	  SUCCESS {

	     emailext body: 'Successfully build and deploy', "Build url:${currentBuild.absoluteUrl}", recipientProviders: [[$class: 'DevelopersRecipientProvider'], [$class: 'RequesterRecipientProvider']], subject: 'Success'

                  }
	  FAILURE {

	     emailext body: 'Build and Deploy Failed', "Build url:${currentBuild.absoluteUrl}", recipientProviders: [[$class: 'DevelopersRecipientProvider'], [$class: 'RequesterRecipientProvider']], subject: 'Failure'

                }
  }
}
	
	

