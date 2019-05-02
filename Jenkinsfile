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

        stage ('tomcat'){
        
            steps{
                sshagent(['tomcat']) {
                    sh 'scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/job-pipeline-project/target/devops.war ec2-user@52.206.18.216:/opt/tomcat/webapps/'
                    }
            }
        }

        stage ('Deployment Stage') {
            steps {
                withMaven(maven : 'maven_3_0_5') {
                    sh 'mvn deploy'
                }
            }
        }
    }
}
