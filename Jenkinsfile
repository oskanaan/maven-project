 pipeline {
   agent any 
   
   stages {
     stage('init'){
       steps {
         sh '''
           export M2_HOME=/home/kanaano/fm/software/apache-maven-3.5.4/
           export PATH=/home/kanaano/fm/software/apache-maven-3.5.4/bin:$PATH
         '''
       }
     }
     stage('Build'){
       steps {
         sh 'mvn clean package'
       }
       post {
         success {
           echo 'Now Archiving....'
           archiveArtifacts artifacts: '**/target/*.war'
         }
       }
     }
   }
 }
