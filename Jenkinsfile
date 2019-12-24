node {
	git url: 'https://github.com/dhivyakiran/helloworld-angular.git'
	mydatas = readYaml file: "sample.yml"
}

pipeline {
	agent
                {
                    
		label 'master'
                            
                }

     	stages 
	{
	stage('Read YML file from another repository') {
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
		when {expression{mydatas.pipeline.steps != "Deploy" }}
		//when{expression{ (mydatas.pipeline.steps == "Build and Deploy") || (mydatas.pipeline.steps == "Build") }}
		 steps {
			   nodejs(nodeJSInstallationName: 'NodeJS'){
    			sh 'npm install'
}
		      }
                }

	    stage('Zip the app')
	    {
		when {expression{mydatas.pipeline.steps != "Deploy" }}    
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
	
	

