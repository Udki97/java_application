pipeline{
        agent any
        stages {
            stage('BuildStarted'){
                steps{
                    notify 'STARTED'
                }
            }
            stage('CloneCode') {
                steps {
                    script {

                        cleanWs()
                        sh "git clone -b ${config.branch} ${config.repoUrl}"

                    }
                }
            }
            stage('setupArtifactory') {
                steps {
                    script {
                        mavenSettingCallFunc {
                            serverID = 'artifactory'
                            credentialID = 'artifactory'
                        }
                    }
                }
            }
            stage('Buildcode') {
                steps {
                    script {
                        sh "cd $path && mvn clean ${config.stage}"

                    }
                }
            }
        }
        post{
            success{
                notify 'SUCCESSFUL'
            }
            failure{

                notify 'FAILED'

            }
        }
}
