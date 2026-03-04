pipeline {
    agent any

    tools {
        maven 'Maven3'
    }

    stages {

        stage('Checkout Code') {
            steps {
                git 'https://github.com/milind55555/Java-maven-jenkins-tomcat-CICD.git'
            }
        }

        stage('Build WAR') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                deploy adapters: [
                    tomcat9(
                        credentialsId: 'tomcat-cred',
                        path: '',
                        url: 'http://13.201.8.234:8080'
                    )
                ],
                contextPath: 'myapp',
                war: '**/*.war'
            }
        }
    }
}
