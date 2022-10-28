pipeline {
    agent any
    tools {
        maven "MAVEN"
        
    }
    stages {
        stage('Initialize'){
            steps{
                echo "PATH = ${M2_HOME}/bin:${PATH}"
                echo "M2_HOME = /opt/maven"
            }
        }
        stage('Build') {
            steps {
                dir("/var/jenkins_home/workspace/demopipelinetask/hello-world-war") {
sh "mvn -Dmaven.test.failure.ignore=true clean package"                }
            }
        }
     
    }
post {
       always {
          junit(
        allowEmptyResults: true,
        testResults: '*/test-reports/.xml'
      )
      }
   } 
}
