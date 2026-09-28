pipeline {
    agent any

    tools {
        jdk 'JDK-21'
        maven 'Maven-3'
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Downloading source code from GitHub'
                git branch: 'main',
                    url: 'https://github.com/Ayush-Gole8/DevOps3'
            }
        }

        stage('Compile') {
            steps {
                echo 'Compiling Java application'
                bat 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                echo 'Executing JUnit tests'
                bat 'mvn test'
            }
        }

        stage('Package') {
            steps {
                echo 'Creating WAR file'
                bat 'mvn package -DskipTests'
                archiveArtifacts artifacts: 'target/*.war',
                    fingerprint: true
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application to Tomcat'
                bat '''
                    copy /Y target\jenkins-demo.war ^
                    "C:\apache-tomcat-11.0.26\webapps\jenkins-demo.war"
                '''
            }
        }

        stage('Verify') {
            steps {
                echo 'Checking deployed application'
                bat '''
                    curl.exe --fail ^
                    http://localhost:8081/jenkins-demo/
                '''
            }
        }
    }

    post {
        always {
            junit allowEmptyResults: true,
                testResults: 'target/surefire-reports/*.xml'
        }

        success {
            echo 'CI/CD PIPELINE SUCCESSFUL'
        }

        failure {
            echo 'CI/CD PIPELINE FAILED'
        }
    }
}
