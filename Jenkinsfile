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
	 sh 'service tomcat8 stop'
	 sh 'cp target/*.war /var/lib/tomcat8/webapps/'
         sh 'service tomcat8 start'	 
	}
	}
}
}
