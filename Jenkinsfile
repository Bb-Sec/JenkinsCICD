pipeline {
    agent any
    environment{
        DOCKER_TAG = getDockerTag()
    }
    stages{
        stage('Build Docker Image'){
            steps{
                sh "sudo docker build . -t fdlynt/example-jenkins:${DOCKER_TAG} ."
            }
        }
        stage('Push Docker Hub'){
            steps{
                withCredentials([string(credentialsId: 'pwd_hub', variable: 'pwd_hub')]) {
                    sh "sudo docker login -u fdlynt -p ${pwd_hub}"
                    sh "sudo docker push fdlynt/example-jenkins:${DOCKER_TAG}"
                }
            }
        }
    }
}