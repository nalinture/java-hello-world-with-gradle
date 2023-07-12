pipeline {
     agent any
     stages {
         stage('Clean Workspace') {
             steps {
                  deleteDir()                  
             }
         }
         stage('Checkout') {
             steps {                  
                  checkout scm                  
             }
         }
         stage('Build') {
             steps {   
                  sh 'chmod +x gradle'
                  sh 'gradle app:installDebug'
                  sh './gradlew clean build'
             }              
             post {
                 always {
                     jiraSendBuildInfo site: 'bashsquad.atlassian.net'
                 }
             }
         }
     }
 }
