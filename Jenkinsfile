pipeline {
    agent any 
        
        tools {
            jdk 'jdk-21'
            maven 'maven-3.9.16'
        }

        stages {
            stage('Checkout') {
                steps {
                    git branch: 'main', 
                    url: 'https://github.com/Shubh168/Maven-app-280626.git'
                }
            }

            stage('Build') {
                steps {
                    sh 'mvn clean compile'
                }
            }

            stage('Test') {
                steps {
                    sh 'mvn test'
                }
            }

            stage('Package') {
                steps {
                    sh 'mvn package'
                }
            }

            stage('Archive') {
                steps {
                    archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
                }
            }
        }

        post {
            success {
                echo 'Build succeeded!'
            }

            failure {
                echo 'Build failed!'
            }

            always {
                echo 'Build completed.'
            }
        }
}