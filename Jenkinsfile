pipeline{
        agent any
        stages {
            stage('BuildStarted'){
                steps{
                    echo 'STARTED'
                }
            }
            /*stage('CloneCode') {
                steps {
                    script {

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
            }*/
            stage('Buildcode') {
                steps {
                    script {
                        sh "mvn clean install"

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
