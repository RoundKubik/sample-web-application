pipeline {

	agent any
		stages {
			stage('Clone Git repository') {
				steps {
					checkout scm
				}
			}
			stage('Build Image') {
				steps {
					sh 'echo Build application image'
					app = docker.build("roundkubik/docker_id", "./Dockerfile")
				}
			}
			stage('Push image to Docker Hub') {
				steps {
						sh 'echo Push image to a Docker Hub'
						docker.withRegistry('https://registry.hub.docker.com', 'docker_id') {
						app.push("latest") 
					}
				}
			}
		
		}
}
