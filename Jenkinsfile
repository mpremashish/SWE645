pipeline{
    agent any
    environment{
        DOCKERHUB_PASS = credentials('DockerPassword')
    }
    stages{
        stage("Checkout"){
            steps{
                checkout scm
                sh 'ls'
                sh 'pwd'
                sh 'cd StudentSurvery/src/main/webapp && jar -cvf studentform.war *'
                sh 'sudo -S docker build --tag mpremashish1/student-survey .'
                sh("echo ${BUILD_TIMESTAMP}")
                withCredentials([usernamePassword(credentialsId: "DockerPassword", passwordVariable: 'PASSWORD', usernameVariable: 'SCHEMA')]) {
                sh 'sudo docker login -u \"$SCHEMA\" -p \"$SCHEMA/$PASSWORD\"'
                }
            }   
        }
        stage("Push docker image"){
            steps{
                sh("sudo docker push mpremashish1/student-survey:${BUILD_TIMESTAMP}")
            }
        }

    }
}
