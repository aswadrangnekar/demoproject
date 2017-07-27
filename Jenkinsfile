pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo '''All prerequisite reside here..
                say,
                - do *-lint/style check
                - compile the app
                - version tagging etc.
                '''
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }

    post {
        always {
            echo 'clean up workspace'
            deleteDir()
        }
        success {
            echo 'I succeeeded!'
            slackSend channel: '#wcdeploy',
                      color: 'good',
                      message: "The pipeline ${currentBuild.fullDisplayName} completed successfully."
        }
        failure {
            echo 'I failed :('
            slackSend channel: '#wcdeploy',
                      color: 'bad',
                      message: "The pipeline ${currentBuild.fullDisplayName} failed."
        }
    }

}