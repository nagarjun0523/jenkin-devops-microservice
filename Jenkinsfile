// Declarative
pipeline {
	agent any
	stages{
		stage('Build') {
			steps {
				echo "Build"
			}
		}
		stage('Test') {
			steps {
				echo "Test"
			}
		}
		stage('Integration Test') {
			steps {
				echo "Integration Test"
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