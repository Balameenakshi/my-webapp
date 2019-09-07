pipeline {

agent { label 'linux-agent-1' }

	tools 
	{ 
	maven "M2_HOME"
	jdk "jdk 1.8"
	}

stages {
	//stage("cloning from git")
	//{
	//steps { git credentialsId: 'Maven-Jar', url: 'https://github.com/Balameenakshi/my-webapp.git' }
	//}

	stage("Build using Maven")
	{
	steps { 
	sh '"/usr/bin/mvn" -Dmaven.test.failure.ignore clean package' }
	}

	stage("Results")
	{
	steps { archiveArtifacts 'target/*.war' 
	}
	}
	//stage("Deploy")
	//{
	//steps {
	//deploy adapters: [tomcat8(credentialsId: 'a7b8f88e-1637-446d-9522-43d948e7ab6d', path: '', url: 'https://192.168.244.128:8080')], contextPath: null, war: '**/*.war'
	//}
	//}
}

}
