pipeline{
    agent any
    environment{
        DOCKERHUB_PASS = credentials('b5f794de-ec19-4a77-97d3-c66da5796d79')
    }
    stages{
        stage("Checkout"){
            steps{
                checkout scm
                sh 'ls'
                sh 'pwd'
                sh 'cd StudentSurvery/src/main/webapp && jar -cvf studentform.war *'
                sh 'sudo -S docker build --tag mpremashish1/student-survey .'
                sh 'echo ${BUILD_TIMESTAMP}'
                sh 'sudo docker login -u mpremashish1 -p ${DOCKERHUB_PASS}'
            }   
        }
        stage("Push docker image"){
            steps{
                sh 'sudo docker push mpremashish1/student-survey:${BUILD_TIMESTAMP}'
            }
        }

    }
}
