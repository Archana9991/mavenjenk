pipeline {

    agent any



    stages {

        stage('Slack it'){

            steps {

                slackSend channel: 'jenkins', 

                          message: 'Hello'

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

}
