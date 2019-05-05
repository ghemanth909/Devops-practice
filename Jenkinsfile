 pipeline {
    agent any

    stages {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'maven_3_0_5') {
                    sh 'mvn clean install'
                }
            }
        }
	    
         stage ('tomcat server deployment'){  
		 steps {
		    sh 'cp target/*.war ec2-user@52.72.244.39:/opt/tomcat/apache-tomcat-8.5.38/webapps'
		    withMaven(maven : 'maven_3_0_5') {
                    sh 'mvn deploy'    
		 }
            }
        }
   }
}
