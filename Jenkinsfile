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
	steps { git credentialsId: 'Maven-Jar', url: 'https://github.com/Balameenakshi/Sample-maven-war-app.git' }
	}

	stage("Build using Maven")
	{
	steps { 
	bat(/"%Maven3%\bin\mvn" -Dmaven.test.failure.ignore clean package/) }
	}

	stage("Results")
	{
	steps { archiveArtifacts 'target/*.war' }
	}
}

}
