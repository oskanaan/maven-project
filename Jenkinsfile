 pipeline {
   agent any 
   
   stages {
     stage('Build'){
       steps {
         sh '''
           export M2_HOME=/home/kanaano/fm/software/apache-maven-3.5.4/
           export PATH=/home/kanaano/fm/software/apache-maven-3.5.4/bin:$PATH
           mvn clean install package
         '''
       }
       post {
         success {
           echo 'Now Archiving....'
           
         }
       }
     }
     stage('deploy to staging'){
       steps{
         build job:'deploy-to-staging'
       }
     }
     stage('deploy to prod'){
       steps{
         timeout(time:5, unit:'DAYS'){
           input message: 'Approve PROD deploy?'
         }
         build job:'deploy-to-staging'
       }
       post {
         success{
           echo 'Code deployed to prod'
         }
         
         failure{
           echo 'Deployment failed'
         }
       }
     }
   }
 }
