pipeline {
    agent any

    environment {
        DOCKERHUB_CREDENTIALS = 'dockerhub-creds'
        IMAGE_NAME = 'karthik19112001/game-app'
    }

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'main',
                url: 'https://github.com/karthikdasaram-OG/website.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME:$BUILD_NUMBER .'
            }
        }

        stage('Push Docker Image') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: "${DOCKERHUB_CREDENTIALS}",
                    usernameVariable: 'DOCKER_USER',
                    passwordVariable: 'DOCKER_PASS'
                )]) {
                    sh '''
                    echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin
                    docker push $IMAGE_NAME:$BUILD_NUMBER
                    docker tag $IMAGE_NAME:$BUILD_NUMBER $IMAGE_NAME:latest
                    docker push $IMAGE_NAME:latest
                    '''
                }
            }
        }

       stage('Deploy to Kubernetes') {
        steps {
        sh '''
        kubectl apply -f deployment.yaml
        kubectl apply -f service.yaml
        '''
    }
}
        stage('Deploy Container') {
            steps {
                sh '''
                docker stop game-app || true
                docker rm game-app || true
                docker run -d --name game-app -p 8080:80 $IMAGE_NAME:latest
                '''
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully!'
        }

        failure {
            echo 'Pipeline failed!'
        }
    }
}
