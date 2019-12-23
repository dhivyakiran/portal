pipeline {
	agent
                {
                    node
                            {
                                label "master"
                            }
                }

      	tools {
  nodejs 'NodeJS'
}

     	stages 
	{
	   stage('Read YML file') {
	      steps 
		{
	          script 
		    {
			  //mydatas = readYaml (file: 'sample.yml')
			    echo "*****************testing*****************"
			
                     }
			
	         }
		}
	    stage('Download Dependencies')
               {
                   steps {
			 nodejs('NodeJS') {
    npm install
}
		      }
                }

	    stage('Zip the app')
	    {
		steps 
		{
	            script
		      {
			zip archive: true, dir: './src', glob: '', zipFile: mydatas.zipfile.filename+"_${currentBuild.number}.zip"
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
	
	

