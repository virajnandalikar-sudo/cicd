pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/virajnandalikar-sudo/cicd.git'
            }
        }
        stage('Run Python Script') {
            steps {
                sh 'python3 hello.py'
            }
        }
        stage('Deploy') {
    steps {
        script {
            // Stop old container if running
            sh 'docker rm -f myapp-container || true'

            // Run new container
            sh 'docker run -d --name myapp-container mydockerhubusername/myapp:latest'
        }
    }
}

    }
    triggers {
        githubPush()
    }
}

