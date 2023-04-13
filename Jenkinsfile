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
		}
}
