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
		stage('Checkout') {
			steps {
				sh "mvn --version"
				sh "docker version"
				echo "Build"
				echo "PATH - $PATH"
				echo "BUILD_NUMBER - $env.BUILD_ID"
				echo "BUILD_TAG - $env.BUILD_TAG"
			}
		}
		stage('Test') {
			steps {
				sh 'mvn test'
			}
		}
		stage('Package') {
			steps {
				sh "mvn package -DskipTests"
			}
		}
		stage('Build Docker Image') {
			steps {
				// "docker build -t in28min/currency-exchange-devops:$env.BUILD_TAG"
				script {
					dockerImage = docker.build("in28min/currency-exchange-devops:latest")
				}
			}
		}
		stage('Push Docker Image') {
			steps {
				script {
					docker.withRegistry('', 'dockerhub') {
						dockerImage.push();
						dockerImage.push('latest');
					}
				}
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