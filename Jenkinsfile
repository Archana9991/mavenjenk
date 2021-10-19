 pipeline {
  tools {
    maven 'Maven3.8.3'
  }
    agent any
    stages {
     stage('Slack it'){

            steps {

                slackSend channel: '#jenkins', 

                          message: 'success'

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
     stage("Deploy to slack"){
            
            
            post {
                success{
                    slackSend channel: '#jenkins', 

                          message: 'success'
                }
                failure{
                     slackSend channel: '#jenkins', 
                      

                          message: 'failure'
                }
            }
    }
 }
