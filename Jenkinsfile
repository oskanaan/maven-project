 pipeline {
   agent any 
   
   parameters {
     string(name: 'tomcat_dev', defaultValue: '54.242.243.169', description: 'staging')
     string(name: 'tomcat_prd', defaultValue: '18.234.181.110', description: 'production')
   }
   
   triggers {
     pollSCM('* * * * *')
   }
   
   stages{
    stage ('Deployments') {
        parallel {
        stage ('Deploy to staging'){
            steps {
            sh "scp -i /home/kanaano/Downloads/tomcat.pem **/*.war ec2-user@${params.tomcat_dev}:/var/lib/tomcat7/webapps"
            }
        }
        stage ('Deploy to prod'){
            steps {
            sh "scp -i /home/kanaano/Downloads/tomcat.pem **/*.war ec2-user@${params.tomcat_prd}:/var/lib/tomcat7/webapps"
            }
        }
        }
    }
   }
 }
