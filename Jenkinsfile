pipeline {
    agent any

    tools {
        maven 'Maven 3.8.1'   // Use the exact name from your Jenkins tool config
        jdk 'JDK 11'          // Replace with the JDK version you configured
    }

    environment {
        REPORT_DIR = "target/surefire-reports"
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/laxman09751/Dev_Gustasi.git'
            }
        }

        stage('Build and Run Tests') {
            steps {
                sh 'mvn clean test'
            }
        }

        stage('Publish Test Reports') {
            steps {
                junit "${REPORT_DIR}/*.xml"
            }
        }
    }

    post {
        success {
            echo '✅ Build and tests succeeded.'
        }
        failure {
            echo '❌ Build or tests failed. Please check the logs.'
        }
        always {
            echo '📦 Pipeline execution completed.'
        }
    }
}
