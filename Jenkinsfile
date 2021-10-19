pipeline {
    agent any

    stages {
        stage('Slack it'){
            steps {
                slackSend channel: '#jenkins', 
                          message: 'Hello, world'
            }
        }
    }
}
