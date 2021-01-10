pipeline {
	agent { docker { image 'maven:3.6.3'} }
	
	stages {
		stage('Build') {

				steps{
					sh 'mvn --version is' 
					echo "Build"
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