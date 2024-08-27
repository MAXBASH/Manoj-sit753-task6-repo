pipeline {
    agent any

    environment {
        EMAIL_RECIPIENT = 'manoz3896@gmail.com'
    }
    stages {
        stage('Build') {
            steps {
                script {
                    echo 'Building the application using build automation tool "Maven"'
                }
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                script {
                    echo 'Running unit and integration tests using test automation tools: "JUnit" for unit tests, "Postman" for integration tests'
                }
            }
            post {
                always{
                    emailext(
                        subject: "Jenkins Pipeline: Unit and Integration Tests - Build Status - ${currentBuild.currentResult}",
                        body: "Jenkins build ${currentBuild.currentResult}: ${env.BUILD_URL}\n",
                        to: "${env.EMAIL_RECIPIENT}",
                        attachLog: true
                    )
                }
            }
        }
        stage('Code Analysis') {
            steps {
                script {
                    echo 'Performing code analysis using "SonarQube"'
                }
            }
        }
        stage('Security Scan') {
            steps {
                script {
                    echo 'Performing security scan using "OWASP Dependency Check"'
                }
            }
            post {
                always{
                    emailext(
                        subject: "Jenkins Pipeline: Security Scan - Build Status - ${currentBuild.currentResult}",
                        body: "Jenkins build ${currentBuild.currentResult}: ${env.BUILD_URL}\n",
                        to: "${env.EMAIL_RECIPIENT}",
                        attachLog: true
                    )
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                script {
                    echo 'Deploying to staging server "AWS EC2 instance"'
                }
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                script {
                    echo 'Running integration tests on staging environment using "Postman"'
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                script {
                    echo 'Deploying to production server "AWS EC2 instance"'
                }
            }
        }
    }
}
