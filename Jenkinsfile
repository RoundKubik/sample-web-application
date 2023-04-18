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
				script {
					docker.withRegistry('https://registry.hub.docker.com', 'roundkubik') {
						app.push("latest") 
					}
				}
			}	
		}
		stage('Run container') {
			steps {
				sh 'echo Run container'
				sh 'ansible-playbook /var/jenkins_home/workspace/test_web_app/docker_playbook.yaml -i /var/jenkins_home/workspace/test_web_app/hosts'
				
			}
		}
		stage('SonarQube analysis') {
			steps {
				sh 'echo Run SAST - SonarQube analysis'
					script {
						def scannerHome = tool 'sonarqube-scanner';
						withSonarQubeEnv("sonar-container") {
							sh "${tool("sonarqube-scanner")}/bin/sonar-scanner \
								-Dsonar.projectKey=WebApp \
								-Dsonar.sources=. \
								-Dsonar.css.node=. \
								-Dsonar.host.url=http://localhost:9000 \
								-Dsonar.login=squ_901744030c31ad28b86e1bd8410b0b15176108ff"
						}
					}
			}
		}
	}
}
