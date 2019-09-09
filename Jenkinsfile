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
	stage("Deploy")
	{
	steps {
	deploy adapters: [tomcat8(credentialsId: 'd7b6d45b-dd3b-4cb4-9155-923e305f5308', path: '', url: 'http://192.168.244.128:8080/')], contextPath: null, war: '**/*.war'
	}
	}
}

}
