node {
     mydatas = readYaml file: "sample.yml"
}

pipeline {
	agent
                {
                    node
                            {
                                label "master"
                            }
                }

     	stages 
	{
	   stage('Read YML file') {
	      steps 
		{
	          script 
		    {
			  
			    echo mydatas.message.test
			
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
			zip archive: true, dir: './src', glob: '', zipFile: mydatas.zipfile.filename+"_${currentBuild.number}.zip"
                      } 
		}
             }
		
	  }
	post {
    always {
	    mail.smtp.starttls.enable=true
       mail to: 'dhivya.krish15@gmail.com',
          subject: "Status of pipeline: ${currentBuild.fullDisplayName}",
          body: "${currentBuild.result}"
    }
  }
}
	
	

