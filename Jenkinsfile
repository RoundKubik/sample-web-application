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
        stage('Deploy pipeline_1') {
			steps {
                echo 'Deploying pipeline_1'
            }
		}
	}
}
