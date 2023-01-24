pipeline {
	agent any
	stages {
		stage('Git clone') {
		    steps {
			    git branch: 'master', credentialsId: 'github-credentials-D', url: 'https://github.com/sanjeev0181/icici.git'
			}
		}
		stage('Mvn builds') {
		    steps {
			sh 'mvn clean package'
			}
		}

	}
}
