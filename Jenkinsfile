pipeline {
    agent any

    tools {
        jdk 'JDK 11'            // Must match your Jenkins JDK installation name
        maven 'maven 3.9.11'    // ✅ Must exactly match what's in Jenkins > Global Tool Config
    }

    stages {
        stage('Checkout Code') {
            steps {
                git url: 'https://github.com/laxman09751/Dev_Gustasi.git', branch: 'main'
            }
        }

        stage('Build and Test') {
            steps {
                sh 'mvn clean test'
            }
        }

        stage('Archive Reports') {
            steps {
                junit 'target/surefire-reports/*.xml'
            }
        }

        stage('Allure Report') {
            steps {
                allure includeProperties: false, results: [[path: 'target/allure-results']]
            }
        }
    }

    post {
        success {
            echo "✅ Build Successful"
        }
        failure {
            echo "❌ Build Failed"
        }
    }
}
