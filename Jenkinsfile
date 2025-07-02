pipeline {
    agent any

    environment {
        MVN_HOME = '/usr/share/maven' // Adjust if needed
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/HarshitaB09/spring-petclinic.git'
            }
        }

        stage('Build') {
            steps {
                sh "${MVN_HOME}/bin/mvn clean package"
            }
        }

        stage('Test') {
            steps {
                sh "${MVN_HOME}/bin/mvn test"
            }
        }

        stage('Archive JAR') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }

    post {
        success {
            echo '✅ Build and test passed!'
        }
        failure {
            echo '❌ Build failed. Check logs.'
        }
    }
}
