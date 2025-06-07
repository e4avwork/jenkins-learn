pipeline {
    agent any
    tools {
        maven 'maven-3.9'
    }
    stages {
        stage('Building the JAR file') {
            steps {
                script {
                    echo "Building the application..."
                    sh 'mvn package'
                }
            }
        }

        stage('Building and Publishing docker image..') {
            steps {
                script {
                withCredentials([usernamePassword(credentialsId: 'shotever', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                    echo "Building docker image..."
                    sh 'docker build -t shotever/java-maven-app:1.0.0 .'
                    echo 'Publishing the docker image...'
                    sh 'echo $DOCKER_PASSWORD | docker login -u $DOCKER_USERNAME --password-stdin'
                    sh 'docker push shotever/java-maven-app:1.0.0'
                }
            }
        }

    }
}