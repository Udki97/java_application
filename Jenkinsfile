pipeline{
       agent any
        tools {
                maven 'maven-latest'
            }
        stages {
            stage('BuildStarted'){
                steps{
                    echo 'STARTED'
                }
            }
            stage('Buildcode') {
                steps {
                    script {
                        withEnv(['MAVEN_HOME = "${tool \'maven-latest\'}"', 'PATH="${MAVEN_HOME}/bin:${PATH}"']) {
                        sh 'mvn clean install'
                        }
                    }
                }
            }
        }
}
