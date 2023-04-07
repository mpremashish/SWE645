pipeline{
    agent any
    stages{
        stage("Checkout"){
            steps{
                checkout scm
                sh 'cd StudentSurvery/src/main/webapp && jar -cvf studentform.war *'
                sh 'sudo docker build --tag mpremashish1/student-survey .'
                sh 'echo ${BUILD_TIMESTAMP}'
            }   
        }
    }
}