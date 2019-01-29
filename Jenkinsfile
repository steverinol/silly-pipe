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
				sh 'rm -f ball.tgz || true'
				sh 'echo "hi ho" > you-know'
				sh 'tar czvf ball.tgz *'
				stash includes: '*.tgz', 
				 name: 'tarball', 
				 useDefaultExcludes: false
				 sh 'rm -f ball.tgz'
				 sh 'rm -f you-know'
			}
		} // end of stage

		stage('show us') {
			steps {
				sh 'ls -l'
			}
		} // end of stage

		stage('develop only') {
			when {
				branch 'develop'
			}
			steps {
				echo 'this is development'
				unstash 'tarball'
				sh 'tar xzvf ball.tgz'
				sh 'rm -f ball.tgz'
				sh 'ls -l'
			}
		} // end of stage

	} // end of stages

	post {
		success {
			fingerprint 'ball.tgz'
		}
	} // end of post

}