pipeline {
    agent any

    stages {
        stage('Checkout') {
    steps {
        git branch: 'main',
            url: 'https://github.com/virajnandalikar-sudo/cicd.git',
            credentialsId: 'cicdnew'
    }
}


        stage('Build Docker Image') {
            steps {
                script {
                    // Build using the Dockerfile inside myapp directory
                    docker.build("virajvn/myapp:latest", "myapp")
                }
            }
        }
        stage('Push to Docker Hub') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'dockerhub-creds') {
                        docker.image("virajvn/myapp:latest").push()
                    }
                }
            }
        }
        stage('Deploy') {
 steps {
        script {
            // Stop old container if running
            sh 'docker rm -f myapp-container || true'

            // Run new container
            sh 'docker run -d --name myapp-container virajvn/myapp:latest'
        }
   }}
}}
