// Declarative
pipeline {
	agent any
	environment {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	// agent { docker{ image 'maven:3.6.3'} }
	stages{
		stage('Build') {
			steps {
				sh "mvn --version"
				sh "docker version"
				echo "Build"
				echo "PATH - $PATH"
				echo "BUILD_NUMBER - $env.BUILD_ID"
			}
		}
	} 
	post{
		always {
			echo 'Im Awesome. I run Always'
		}
		success {
			echo 'I run when your are Success'
		}
		failure {
			echo 'I run when your are Failure'
		}
	}	
}