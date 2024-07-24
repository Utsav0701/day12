pipeline {
    agent any

    environment {
        MAVEN_HOME =tool 'Maven-3.9.0'
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/Utsav0701/day12.git', branch: 'main'
            }
        }

        stage('BUild') {
            steps {
                script {
                    withEnv(["PATH+MAVEN=${MAVEN_HOME}\\bin"]) {
                        sh 'mnv clean package'
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
            echo 'Finished.'
        }
        success {
            echo 'Succeeded'
        }
        failure {
            echo 'failed'
        }
    }
}
