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
                  sh 'chmod +x ./gradlew'
                  sh './gradlew app:installDebug'
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
