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
		stage("Sonarqube Build Analysis") {
            steps {
                script {
                    withSonarQubeEnv(credentialsId: 'sonar-token') {
                    sh 'mvn sonar:sonar'
                    }
                }
            }
		}
	    stage("Sonarqube Qunatity Gate") {
            steps {
                script {
		             waitForQualityGate abortPipeline: false, credentialsId: 'sonar-token' 
                    }
            }
        }
		stage('docker login') {
				steps {
					withCredentials([string(credentialsId: 'Dockerfile-DD', variable: 'Dockerfile-s')]) {
						sh "docker login -u sanjeev0181 -p  ${Dockerfile-s}"
				    }
				
				}
			}
	        
    }
}

