pipeline{
        agent any
        tools {
        withMaven( 'maven-default')
        }
        //withMaven(maven: 'apache Maven 3.3.9')
        stages {
            stage('BuildStarted'){
                steps{
                    echo 'STARTED'
                }
            }
            stage('CloneCode') {
                steps {
                    script {

                        sh "git clone -b ${config.branch} ${config.repoUrl}"

                    }
                }
            }
            stage('setupArtifactory') {
                steps {
                    script {
                        def server = Artifactory.server artifactory
                        def credentials = Artifactory.credentials artifactory
                        }
                    }
                }
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
