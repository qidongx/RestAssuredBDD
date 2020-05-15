pipeline {
	agent any
	stages {
		stage('Checkout project from GitHub') {
			steps {
				git 'https://github.com/qidongx/RestAssuredBDD.git';
				echo "Code checked out from GitHub successfully!";
			}		
		}
		stage('Build') {
			steps {
				sh label: '', script: './build.sh';   //MUST have "./" in front of filename in order for the shell to find it.
				echo "Compiled using build.sh successfully!";
			}
		}
		stage('Unit Test') {
			steps {
				sh label: '', script: './unitest.sh';
				echo "JUnit test passed successfully!";
			}
		}
		stage('Regression Test'){
			steps {
				sh label: '', script: './regressionTest.sh';
				echo "Regression test passed successfully!";
			}
		}
		stage("Parallel performance test.") {
			parallel {
				stage('Test on Master'){
					agent {
						label "master"
					}
					steps {
						echo "Running on master."
					}
				}
				stage('Test on slave') {
					agent {
						label "node1"
					}
					steps {
						echo "Running on slave."
					}
				}
			}
		}
		stage('Deploy'){
			steps {
				sh label: '', script: './deploy.sh';
				echo "Deployed successfully!";
			}
		}
	}
	post {
		always {
			echo 'This will always run.'
		}
		success {
			echo 'This will run only if success.'
		}
		failure {
			echo 'This will run only if failed.'
		}
		unstable {
			echo 'This will run only if the run is marked as unstable.'
		}
		changed {
			echo 'This will run only if the state of the pipeline has changed.'
			echo 'For example, if the pipeline was previously failing but now is successful.'
		}
	}
}
