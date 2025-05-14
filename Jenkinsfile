pipeline {
    agent {
        docker {
            image 'maven:3.9.6-eclipse-temurin-17'
            args '-v /root/.m2:/root/.m2'  // optional: cache maven dependencies
        }
    }

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/Mo-Faraan/Maven4Jenkins.git'
            }
        }

        stage('Build Package') {
            steps {
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
