pipeline {
	agent any
	//agent { docker { image 'maven:3.6.3'} }
	//agent { docker { image 'node:13.8'} }

	environment {
		dockerHOME = tool 'myDocker' //Ensure Docker Insallation is setup in GLobal Tool config with name as "myDocker"
		mavenHOME = tool 'myMaven' //Ensure Maven Insallation is setup in GLobal Tool config with name as "myMaven"
		PATH = "$dockerHOME/bin:$mavenHOME/bin:$PATH"
		
	}

	stages {
		
		stage('Code Checkout') 
			{
				steps{
						sh 'mvn --version' 
						sh 'docker version' 
						//sh 'node --version is' 
						echo "Build URL is ${env.BUILD_URL}"
						echo "Build PAth is  $PATH"
						echo "Build Number is ${env.BUILD_NUMBER}"
						echo "Build ID is ${env.BUILD_ID}"
						echo "Job Name is ${env.Job_NAME}"
						echo "Build Tag is ${env.BUILD_TAG}"
					}
				}

		stage('Compile') 
		{
			steps{  
				echo "Code compile is running"
				sh "mvn clean compile"
			}
		}

		stage('Test') {

				steps{
					echo "Test is Running"
					sh "mvn test"
					}
				}	

		stage('Integration Test') {

				steps{
					echo "Integration Test is running"
					sh "mvn failsafe:integration-test failsafe:verify"
				}
		}

		stage('Package') {

				steps{
					echo "Binary is being created"
					sh "mvn package -DskipTests"
				}
		}
		
		stage('Build Docker Image') {

				steps{
					echo "Docker Build"
					//docker build -t 16022011/currency-exchange-devops:${env.BUILD_TAG}
					script{
						dockerImage=docker.build("16022011/currency-exchange-devops:${env.BUILD_TAG}")
					}

				}
		}

		stage('Push Docker Image') {

				steps{
					echo "Docker Push"
					//docker build -t 16022011/currency-exchange-devops:${env.BUILD_TAG}
					script{
						docker.withRegistry('','dockerhub'){ //ensure Docker ID is configued with user as "dockerhub" in credentials 
						dockerImage.push();
						dockerImage.push('latest');
					}
					}

				}
		}
	} 

	post {
		always {
					echo 'Always Learning a lot more'
				}
		success {
					echo 'Succesful build'
				}
		failure {
					echo 'Failure build'
				}
		changed {
					echo 'changed build'
				}
		unstable {
					echo 'unstable build'
				}

	}
}