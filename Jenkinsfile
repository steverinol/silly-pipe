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
		}
		stage('create a file') {
			steps {
				sh 'echo "hi ho" > you-know'
				sh 'tar czvf ball.tgz'
			}
		}
		stage('show us') {
			steps {
				sh 'ls -l'
			}
		}
		post {
			success {
				fingerprint 'ball.tgz'
			}
		}
	}
}