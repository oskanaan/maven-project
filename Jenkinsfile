 pipeline {
   agent any 
   
  
   stages{
    stage ('Build') {
        steps {
          sh '''
            export M2_HOME=/home/kanaano/fm/software/apache-maven-3.5.4/
            export PATH=/home/kanaano/fm/software/apache-maven-3.5.4/bin:$PATH
            mvn clean package
          '''
        }
    }
   }
 }
