pipeline {
	agent any
	stages {
		stage('Checkout SCM') {
			steps {
				//sh 'ls'
				//sh 'cd ..'
				//sh 'ls'
				git './'
			}
		}

		stage('OWASP DependencyCheck') {
			steps {
				dependencyCheck additionalArguments: '--format HTML --format XML', odcInstallation: 'Default'
			}
		}
	}	
	post {
		success {
			dependencyCheckPublisher pattern: 'dependency-check-report.xml'
		}
	}
}