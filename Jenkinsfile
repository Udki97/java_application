pipeline{
        agent any
         tools {
                maven 'maven-latest'
            }
        environment {
            MAVEN_HOME = "${tool 'maven-latest'}"
            PATH="${MAVEN_HOME}/bin:${PATH}"
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
            /*stage('setupArtifactory') {
                steps {
                    script {
                        def server = Artifactory.server artifactory
                        def credentials = Artifactory.credentials artifactory
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
