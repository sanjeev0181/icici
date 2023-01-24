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
		    stage("Docker Builds") {
				steps {
					sh 'docker build -t sanjeev0181/funds-1.0.war  -f   /opt/Dockerfile .'
				}
			}
			stage('pushing docker image') {
				steps {
					sh "docker login -u sanjeev0181 -padityasanjeev"
					sh "docker push sanjeev0181/funds-1.0.war "
				}
			}
		}
	}
