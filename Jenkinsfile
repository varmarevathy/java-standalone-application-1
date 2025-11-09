pipeline {
    agent any

    tools {
        jdk 'JDK17'
        maven 'Maven3'
    }

    stages {
        stage('Checkout') {
            git branch: 'br-a-file-change', url: 'https://github.com/varmarevathy/java-standalone-application-1'
        }
        stage('Build') {
            // write your logic here
            sh 'mvn clean package'
        }
        stage('Run Application') {
            // write your logic here
            sh 'java -jar target/java-standalone-application-1.0-SNAPSHOT.jar'
        }
        stage('Test') {
            // write your logic here
            steps{
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
    }
}
