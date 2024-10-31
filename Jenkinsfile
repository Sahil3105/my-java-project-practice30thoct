pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                // Clean and build the project
                sh 'mvn clean install'
            }
        }
        stage('Test') {
            steps {
                // Run unit tests and generate reports
                sh 'mvn test'
            }
        }
        stage('Archive') {
            steps {
                // Archive the JAR file and test results
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
                junit 'target/surefire-reports/*.xml'
            }
        }
    }
    post {
        always {
            // Clean up workspace
            cleanWs()
        }
    }
}
