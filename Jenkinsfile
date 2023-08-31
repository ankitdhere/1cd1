pipeline {
    agent any

    environment {
        NODEJS_HOME = tool name: 'NodeJS', type: 'jenkins.plugins.nodejs.tools.NodeJSInstallation'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build and Test') {
            steps {
                script {
                    def nodeCommand = "${NODEJS_HOME}/bin/node"
                    def npmCommand = "${NODEJS_HOME}/bin/npm"

                    sh "${npmCommand} install"
                    sh "${npmCommand} test"
                }
            }
        }
    }

    post {
        always {
            junit '**/test-reports/*.xml'
        }
    }
}
