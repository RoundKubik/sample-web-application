pipelineJob {
    definition {
        cps {
            script('''
        node {
            stage('Build pipeline_1') {
                echo 'Building pipeline_1\'
            }
            stage('Test pipeline_1') {
                echo 'Testing pipeline_1\'
            }
            stage('Deploy pipeline_1') {
                echo 'Deploying pipeline_1\'
            }
        }
      '''.stripIndent())
            sandbox()
        }
    }
}



