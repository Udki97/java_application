pipeline{
        agent any
         tools {
                maven 'maven-latest'
                jdk 'java-default'
            }
        /*environment {
            MAVEN_HOME = "${tool 'maven-latest'}"
            PATH="${MAVEN_HOME}/bin:${PATH}"
        }*/
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
                        //withEnv(['MAVEN_HOME = "${tool \'maven-latest\'}"', 'PATH="${MAVEN_HOME}/bin:${PATH}"']) {
                        sh 'mvn clean install'
                        //}
                    }
                }
            }
        }
        post {
            success {
                echo 'SUCCESSFUL'
            }
            failure {

                echo 'FAILED'

            }
        }
}
