pipeline{
    agent any
    environment{
        DOCKERHUB_PASS = credentials('password_docker')
    }
    stages{
        stage("Checkout"){
            steps{
                checkout scm
                sh 'ls'
                sh 'pwd'
                sh 'cd StudentSurvery/src/main/webapp && jar -cvf studentform.war *'
                sh("sudo -S docker build --tag mpremashish1/student-survey:${BUILD_TIMESTAMP} .")
                sh("echo ${BUILD_TIMESTAMP}")
                sh('sudo docker login -u mpremashish1 -p \"${DOCKERHUB_PASS}\"')
            }   
        }
        stage("Push docker image"){
            steps{
                sh("sudo docker push mpremashish1/student-survey:${BUILD_TIMESTAMP}")
            }
        }

    }
}
