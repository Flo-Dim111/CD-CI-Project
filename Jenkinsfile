pipeline {
    agent any
    environment {
        DOCKER_IMAGE_NAME = "fastapi_app"
    }
    stages {
        stage('Build') {
            steps {
                script {
                    // Build Docker image for FastAPI app
                    docker.build(DOCKER_IMAGE_NAME, "-f Dockerfile .")
                    
                    // Run FastAPI app container
                    docker.image(FASTAPI).run("-d -p 8000:8000 --name fastapi_container")
                }
            }
        }
        stage('Test'){
            steps {
                echo 'testing the application'
                // You can add your testing steps here
            }
        }
        stage('Deploy') {
            steps {
                echo 'deploying the application'
                // You can add your deployment steps here
            }
        }
    }
   
}
