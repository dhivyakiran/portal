@Grab('org.yaml:snakeyaml:1.17')
import org.yaml.snakeyaml.Yaml
import org.yaml.snakeyaml.DumperOptions
import static org.yaml.snakeyaml.DumperOptions.FlowStyle.BLOCK

node {
    def yaml = readYaml file: "sample.yml"
}
pipeline {
   agent any
	stages {
		stage('Read YML file') {
			steps 
			{
				echo yaml.message.test
			}
		}
	}
}
