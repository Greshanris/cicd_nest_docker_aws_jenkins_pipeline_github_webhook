pipeline {
    agent any

    environment {
        CONTAINER_NAME = "nestjs-app"
        IMAGE_NAME = "nestjs-image"
        EMAIL = "rishavc957@gmail.com"
        PORT = "3000"
    }

    stages {
        stage ('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/Greshanris/cicd_nest_docker_aws_jenkins_pipeline_github_webhook.git'
            }
        }

        stage ('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage ('Stop & Remove Previous Container') {
            steps {
                sh '''
                    docker stop $CONTAINER_NAME || true
                    docker rm $CONTAINER_NAME || true
                '''
            }
        }

        stage ('Docker Container Run ') {
            steps {
                sh '''
                    docker run -d -p ${PORT}:${PORT} --name $CONTAINER_NAME $IMAGE_NAME
                '''
            }
        }

        stage ('Send Email Notifications') {
            steps {
                emailtext(
                    subject: "NestJS App Deployed Successfully on EC2!",
                    body: "Your Nest JS app is Deployed! http://54.66.27.152:${PORT}",
                    to: "${EMAIL}"
                )
            }
        }
    }
}