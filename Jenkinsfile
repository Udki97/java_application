pipeline{
        agent any
        stages {
            stage('BuildStarted'){
                steps{
                    echo 'STARTED'
                }
            }
            stage('CloneCode') {
                steps {
                    script {

                        cleanWs notFailBuild: true
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
                echo 'SUCCESSFUL'
            }
            failure{

                echo 'FAILED'

            }
        }
}
