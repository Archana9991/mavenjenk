 pipeline {
  tools {
    maven 'Maven3.8.3'
  }
    agent any
    stages {
     stage('Slack it'){

            steps {

                slackSend channel: '#marketing', 

                          message: 'Hello, world'

            }

        }
     
        stage('Clean') {
            steps {
                echo 'Cleaning..'
                bat 'mvn -B -DskipTests clean'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
                bat 'mvn test'
            }
             post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Package') {
            steps {
                echo 'mvn package'
            }
        }
    }
  
