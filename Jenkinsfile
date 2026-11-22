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
                git branch: 'main', url: ''
            }
        }
    }
}