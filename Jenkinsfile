pipeline {
    agent any
    environment {
        DOCKER_HUB_REPO = "abhishekkumargaya/flask_test"
        CONTAINER_NAME = "flask-container"
    }
    stages {
        stage('Build') {
            steps {
                //  Building new image
                sh 'docker image build -t $DOCKER_HUB_REPO:latest .'
                sh 'docker image tag $DOCKER_HUB_REPO:latest $DOCKER_HUB_REPO:$BUILD_NUMBER'

                //  Pushing Image to Repository
                sh 'docker push $DOCKER_HUB_REPO:$BUILD_NUMBER'
                sh 'docker push $DOCKER_HUB_REPO:latest'

                echo "Image built and pushed to repository"
            }
        }
        stage('Deploy') {
            steps {
                script{
                    echo 'Testing Deploy'
                }
            }
        }
    }
}