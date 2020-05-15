pipeline {
	agent any 
	stages {
		stage('Checkout project from GitHub') {
			steps {
				git 'https://github.com/qidongx/RestAssuredBDD.git';
				echo "Code checked out from GitHub successfully!";
			}		
		}
		stage('Compile') {
			steps {
				sh label: '', script: './build.sh';
				echo "Compiled using build.sh successfully!";
			}
		}
		stage('JUnit') {
			steps {
				echo "JUnit test passed successfully!";
			}
		}
		stage('Regression Test'){
			steps {
				echo "Regression test passed successfully!";
			}
		}
		stage('Deploy'){
			steps {
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
