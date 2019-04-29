pipeline {
    agent none

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                mavenWith(maven: 'maven_3_6_1')
                sh 'mvn clean compile'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
               mavenWith(maven: 'maven_3_6_1')
                sh 'mvn test'
              }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                mavenWith(maven: 'maven_3_6_1')
               sh 'mvn deploy'
            }
        }
    }
}
