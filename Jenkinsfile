pipeline{
    agent any
    stages{
        stage("Checkout"){
            steps{
                checkout scm
                sh 'ls'
                sh 'cd StudentSurvery/src/main/webapp && jar -cvf studentform.war *'
                sh 'echo "admin" | sudo -S docker build --tag mpremashish1/student-survey .'
                sh 'echo ${BUILD_TIMESTAMP}'
            }   
        }
    }
}
