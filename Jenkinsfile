pipeline {
	agent any
	//agent { docker { image 'maven:3.6.3'} }
	//agent { docker { image 'node:13.8'} }
	stages {
		stage('Build') {

				steps{
					//sh 'mvn --version is' 
					//sh 'node --version is' 
					echo "Build URL is ${env.BUILD_URL}"
					echo "Build PAth is  $PATH"
					echo "Build Number is ${env.BUILD_NUMBER}"
					echo "Build ID is ${env.BUILD_ID}"
					echo "Job Name is ${env.Job_NAME}"
					echo "Build Tag is ${env.BUILD_TAG}"
					}
				}

		stage('Test') {

				steps{
					echo "Test"
					}
				}	

		stage('Integration Test') {

				steps{
					echo "Integration Test"
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