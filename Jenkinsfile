pipeline {
	agent any
	stages {
		stage('Clone Git repository') {
			steps {
				checkout scm
			}
		}
        stage('Test pipeline_1') {
            steps {
			   echo 'Testing pipeline_1'
            }
		}
        stage('Deploy pipeline_1') {
			steps {
                echo 'Deploying pipeline_1'
            }
		}
	}
}
