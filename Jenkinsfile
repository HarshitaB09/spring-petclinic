pipeline {
    agent any  // run on any available agent

    environment {
        MVN_HOME = '/usr/share/maven' // Adjust to your Maven path
    }

    stages {
        stage('Clone Repo') {
            steps {
                git url: 'https://github.com/spring-projects/spring-petclinic.git'
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

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Build finished successfully!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
