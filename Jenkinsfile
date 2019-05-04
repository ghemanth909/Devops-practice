 pipeline {
    agent any

    stages {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'maven_3_0_5') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'maven_3_0_5') {
                    sh 'mvn test'
                }
            }
        }
	    
         stage ('tomcat server deployment'){  
		    archive 'target/*.war'  
	            scp 'target/*.war /opt/tomcat/apache-tomcat-8.5.38/webapps' 
		    withMaven(maven : 'maven_3_0_5') {
                    sh 'mvn deploy'     
            }
        }
   }
}
