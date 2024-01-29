pipeline {
    agent any

    stages{
        stage('fetch code') {
          steps{
              git branch: 'vp-rem', url: "https://github.com/tamzilsre/codenew.git"
          }  
        }

        stage('Build') {
            steps {
                sh 'mvn clean install -DskipTests'
            }
            post {
                success {
                    echo "Now Archiving."
                    archiveArtifacts artifacts: '/var/lib/jenkins/workspace/29jansampleproject/target/*.war
'
                }
            }
        }
        stage('Test'){
            steps {
                sh 'mvn test'
            }

        }
         stage('Code Ananlysis'){
            steps {
                sh 'mvn checkstyle:checkstyle'
            }

        }
    }
}
