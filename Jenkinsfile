pipeline {
    agent any
    environment {
        MAVEN_HOME = tool 'Maven-3.9.0'
    }
    parameters {
        string(name: 'MAVEN_GOALS', defaultValue: 'clean install', description: 'Maven goals to execute')
        string(name: 'MAVEN_OPTIONS', defaultValue: '', description: 'Additional Maven options')
    }
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/Utsav0701/day12.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                script {
                    withEnv(["PATH+MAVEN=${MAVEN_HOME}/bin"]) {
                        sh "mvn ${params.MAVEN_OPTIONS} ${params.MAVEN_GOALS}"
                    }
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    echo 'Test Done'
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
