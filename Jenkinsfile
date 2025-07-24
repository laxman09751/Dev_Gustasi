pipeline {
    agent any

    tools {
        jdk 'JDK 11'
        maven 'Maven 3.8.1'
    }

    stages {
        stage('Checkout Code') {
            steps {
                git url: 'https://github.com/<your-username>/Dev_Gustasi.git', branch: 'main'
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
            echo "Build Successful"
        }
        failure {
            echo "Build Failed"
        }
    }
}
