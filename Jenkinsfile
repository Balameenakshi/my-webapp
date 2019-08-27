pipeline {

agent { label 'master' }

	tools 
	{ 
	maven "Maven3"
	jdk "jdk 1.8"
	}

stages {
	stage("cloning from git")
	{
	steps { git credentialsId: 'Maven-Jar', url: 'https://github.com/Balameenakshi/my-webapp.git' }
	}

	stage("Build using Maven")
	{
	steps { 
	bat(/"%Maven3%\bin\mvn" -Dmaven.test.failure.ignore clean package/) }
	}

	stage("Results")
	{
	steps { archiveArtifacts 'target/*.war' 
	deploy adapters: [tomcat8(credentialsId: 'd7b6d45b-dd3b-4cb4-9155-923e305f5308', path: '', url: 'http://localhost:8087')], contextPath: null, war: 'Webapp.war'
	}
	}
}

}
