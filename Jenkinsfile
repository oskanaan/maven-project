 pipeline {
   agent any 
   
   stages {
     stage('Build'){
       steps {
         sh '''
           export M2_HOME=/home/kanaano/fm/software/apache-maven-3.5.4/
           export PATH=/home/kanaano/fm/software/apache-maven-3.5.4/bin:$PATH
           mvn clean package
         '''
       }
       post {
         success {
           echo 'Now Archiving....'
           archiveArtifacts artifacts: '**/target/*.war'
         }
       }
     }
     stage('deploy to staging'){
       steps{
         build job:'deploy-to-staging'
       }
     }
   }
 }
