pipeline{
        agent any
         tools {
                maven 'maven-latest'
            }
        /*environment {
            MAVEN_HOME = "${tool 'maven-latest'}"
            PATH="${MAVEN_HOME}/bin:${PATH}"
        }*/
        withEnv(['MAVEN_HOME = "${tool \'maven-latest\'}"', 'PATH="${MAVEN_HOME}/bin:${PATH}"']) {

        stages {
            stage('BuildStarted'){
                steps{
                    echo 'STARTED'
                }
            }
            stage('CloneCode') {
                steps {
                    script {
                        checkout scm
                    }
                }
            }
            stage('Buildcode') {
                steps {
                    script {
                        sh 'mvn clean install'
                    }
                }
            }
            stage('Test')
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
}
