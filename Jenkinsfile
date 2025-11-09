pipeline {
    agent any

    tools {
        jdk 'Java_21'
        maven 'maven_3.9'
    }

    stages {
        stage('Checkout') {
            steps {
                // checkout a specific branch from the repo
                git branch: 'br-a-file-change-123', url: 'https://github.com/varmarevathy/java-standalone-application-1'
            }
        }
        stage('Build') {
            steps {
                // build the project
                sh 'mvn clean package'
            }
        }
        /*stage('Run Application') {
            steps {
                // run the packaged jar (adjust path/name as appropriate)
                sh 'java -jar target/java-standalone-application-1.0-SNAPSHOT.jar'
            }
        }*/
        stage('Test') {
            steps {
                // run tests
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
