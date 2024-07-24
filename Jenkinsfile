pipeline {
    agent any
    tools {
        maven 'Maven-3.9.0' // Use the name configured in Global Tool Configuration
    }
    stages {
        stage('Checkout') {
            steps {
                // Checkout code from GitHub repository
                git url: 'https://github.com/Utsav0701/day12.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                // Build the project using Maven
                script {
                    withEnv(["PATH+MAVEN=${MAVEN_HOME}/bin"]) {
                        sh 'mvn clean install'
                    }
                }
            }
        }
        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: '**/target/*.jar', allowEmptyArchive: true
            }
        }
    }
    post {
        always {
            echo 'Pipeline finished.'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
