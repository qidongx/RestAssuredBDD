pipeline {
	agent {
		label 'node1'
	} 
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
		stage('Unit Testing') {
			steps {
				sh label: '', script: './unitest.sh';
				echo "JUnit test passed successfully!";
			}
		}
		stage('Regression Testing'){
			steps {
				sh label: '', script: './regressionTest.sh';
				echo "Regression test passed successfully!";
			}
		}
		stage('Deploying'){
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
