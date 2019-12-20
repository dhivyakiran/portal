pipeline {
   agent
   {
	node 
		{
			datas = readYaml file: 'sample.yaml'
		}
	}
	stages {
		stage('Read YML file') {
			steps 
			{
				echo ${datas.test}
			}
		}
	}
}