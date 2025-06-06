pipeline {
    agent any

    tools {
        maven 'Maven 3.8.6' // This name must match what's set in Jenkins > Global Tool Config
        jdk 'Java 17'       // Same here
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Bindu-Harshitha/spring-petclinic.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install -DskipTests'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
            }
        }
    }
}
