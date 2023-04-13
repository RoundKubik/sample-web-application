pipeline {
	agent any
	stages {
		stage('Clone Git repository') {
			steps {
				checkout scm
			}
		}
        stage('Build image') {
            steps {
				sh 'echo Build application image'
					script {
						app = docker.build("roundkubik/docker_id", "./Dockerfile")
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
