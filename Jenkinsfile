pipeline {

	options {
	  buildDiscarder logRotator(
	  	artifactDaysToKeepStr: '', 
	  	artifactNumToKeepStr: '', 
	  	daysToKeepStr: '', 
	  	numToKeepStr: '6')
	}

	agent any 

	stages {

		stage('preparation h') {
			steps {
				echo 'preparing for it'
			}
		} // end of stage

		stage('create a file') {
			steps {
				sh 'echo "hi ho" > you-know'
				sh 'tar czvf ball.tgz'
			}
		} // end of stage

		stage('show us') {
			steps {
				sh 'ls -l'
			}
		} // end of stage
		
	} // end of stages

	post {
		success {
			fingerprint 'ball.tgz'
		}
	}
}