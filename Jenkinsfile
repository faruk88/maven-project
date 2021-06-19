pipeline{
	agent any
	environment{
		PATH = "/opt/maven-3/bin:$PATH"
	}
	stages{
		stage("Git Checkout"){
			steps{
			git 'https://github.com/faruk88/maven-project.git'	
			}
		}
		stage("Maven Build"){
			steps{
			sh "mvn clean package"	
			sh "mv target/*.jar target/myweb.jar"
			}
		}
		stage("Deploy-Dev"){
			steps{
			sshagent(['tomcat-8']) {
    				sh """
					scp -o StrictHostKeyChecking=no target/myweb.jar root@192.168.1.60:/opt/tomcat8/webapps/
					ssh root@192.168.1.60 /opt/tomcat8/bin/shutdown.sh
					ssh root@192.168.1.60 /opt/tomcat8/bin/startup.sh
				"""
			}			
			}
		}
	}
}
