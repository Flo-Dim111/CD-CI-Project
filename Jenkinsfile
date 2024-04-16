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
    post {
        always {
            // Clean up: Stop and remove the container after the pipeline finishes
            script {
                docker.image(DOCKER_IMAGE_NAME).stop()
                docker.image(DOCKER_IMAGE_NAME).remove(force: true)
            }
        }
    }
}
