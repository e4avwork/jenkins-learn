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
    }
}