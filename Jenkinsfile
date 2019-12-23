pipeline {
	agent
                {
                    node
                            {
                                label "slave1"
                            }
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
                       sh 'npm install'
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
	
	

