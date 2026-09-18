pipeline {

    agent any

    tools {
        jdk 'JDK-17'
        maven 'Maven-3.9'
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
                echo 'Building Java project...'
                bat 'mvn clean compile'
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
                echo 'Creating JAR file...'
                sh 'mvn package -DskipTests'
            }
        }
    }

    post {

        success {
            echo 'BUILD SUCCESSFUL!'
            echo 'Electricity Bill project passed all tests.'
        }

        failure {
            echo 'BUILD FAILED!'
            echo 'Please check the Jenkins console output.'
        }

        always {
            echo 'Pipeline execution completed.'
        }
    }
}
