@Library(['github.com/indigo-dc/jenkins-pipeline-library@fix/pull_always]) _

def projectConfig

pipeline {
    agent any

    stages {
        stage('SQA baseline criterion: QC.Acc & QC.Doc & QC.Lic & QC.Met & QC.Sec & QC.Sty & QC.Ver') {
            steps {
                script {
                    projectConfig = pipelineConfig(
                        configFile: '.sqa/config.yml',
                        scmConfigs: [ localBranch: true ],
                        validatorDockerImage: 'eoscsynergy/jpl-validator:2.4.0'
                    )
                    buildStages(projectConfig)
                }
            }
            post {
                cleanup {
                    cleanWs()
                }
            }
        }
    }
}
