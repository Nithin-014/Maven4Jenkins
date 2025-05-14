pipeline {
    agent {
        docker {
            image 'maven:3.9.6-eclipse-temurin-17'
            args '-v /root/.m2:/root/.m2'  // optional: cache maven dependencies
        }
    }

    environment {
        // You can set environment variables here if needed
    }

    stages {
        stage('Checkout Code') {
            steps {
                // Clone the repo
                git 'https://github.com/Mo-Faraan/Maven4Jenkins.git'
            }
        }

        stage('Build Package') {
            steps {
                // Clean and package the Maven project
                sh 'mvn clean package'
            }
        }

        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Build completed successfully!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
