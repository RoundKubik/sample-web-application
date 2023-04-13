pipeline {
	agent any
	stages {
		stage('Clone Git repository') {
			steps {
				checkout scm
			}
		}
		stage('Build project') {
			steps {
				sh 'mvn clean package'
			}
		}
        stage('Build image') {
            steps {
				sh 'echo Build application image'
					script {
						app = docker.build("roundkubik/docker_id")
					}
            }
		}
		stage('Push image to Docker Hub') {
			steps {
				sh 'echo Push image to a Docker Hub'
				scipt {
					docker.withRegistry('https://registry.hub.docker.com', 'docker_id') {
						app.push("latest") 
					}
				}
			}	
		}
        stage('Deploy pipeline_1') {
			steps {
                echo 'Deploying pipeline_1'
            }
		}
	}
}
