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
	    
	    stage ('Testing Stage') {
            steps {
                withMaven(maven : 'maven_3_0_5') {
                    sh 'mvn test'
                }
            }
        }
	    
             stage ('tomcat server deployment'){  
		 steps {
		    sh 'cp /var/lib/jenkins/workspace/job-pipeline-project/target/*.war /opt/tomcat/apache-tomcat-8.5.38/webapps'
		    //sh 'emailext body: '', subject: 'Devops', to: 'ghemanth909@gmail.com; devopstest080@gmail.com''
            }
        }
   }
}
