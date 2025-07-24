<<<<<<< HEAD
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
=======
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
>>>>>>> 885416f (Fix: Updated POM and other test files)
