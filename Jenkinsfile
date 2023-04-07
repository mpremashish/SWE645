pipeline{
    agent any
    // environment{
    //     DOCKERHUB_PASS = credentials('docker-pass')
    // }
    stages{
        stage("Checkout"){
            steps{
                checkout scm
                sh 'ls'
                sh 'pwd'
                sh 'cd StudentSurvery/src/main/webapp && jar -cvf studentform.war *'
                sh 'sudo -S docker build --tag mpremashish1/student-survey .'
                sh 'echo ${BUILD_TIMESTAMP}'
                // sh 'docker login -u mpremashish1 -p '
            }   
        }

    }
}
