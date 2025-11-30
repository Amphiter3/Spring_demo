pipeline {
    agent {
        docker {
            image 'maven:3.9.4-eclipse-temurin-17'
            args '-u root:root'
        }
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out source code...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building the project with Maven...'
                sh 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                echo 'Running JUnit tests...'
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                echo 'Packaging the Spring Boot application...'
                sh 'mvn package'
            }
        }
    }

    post {
        success {
            echo 'Build, test, and packaging completed successfully!'
        }
        failure {
            echo 'Something went wrong. Check the console output for errors.'
        }
    }
}
