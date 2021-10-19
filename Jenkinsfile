 pipeline {
  tools {
    maven 'Maven3.8.3'
  }
    agent any
    stages {
     stage('Slack it'){

            steps {

                slackSend channel: '#jenkins', 

                          message: 'started'

            }

        }
     
        stage('Clean') {
            steps {
                echo 'Cleaning..'
                bat 'mvn -B -DskipTests clean'
            }
         post{
            
            
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
         post{
            
            
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
 }
