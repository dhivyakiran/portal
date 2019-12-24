node {
     mydatas = readYaml file: "sample.yml"
}

pipeline {
	agent
                {
                    
		label datas.agentdetail.agentname
                            
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
			zip archive: true, dir: './src', glob: '', zipFile: mydatas.zipfile.filename+"_${currentBuild.number}.zip"
                      } 
		}
             }
		
	  }
	post {
	  success {
		  mail to: 'dhivya.k@cognizant.com',
          subject: "Success pipeline: ${currentBuild.fullDisplayName}",
          body: "${currentBuild.absoluteUrl} has result ${currentBuild.result}"

	        }
	  failure {

	     mail to: 'dhivya.krish15@gmail.com',
          subject: "Failure pipeline: ${currentBuild.fullDisplayName}",
          body: "${currentBuild.absoluteUrl} has result ${currentBuild.result}"

                }
  }
}
	
	

