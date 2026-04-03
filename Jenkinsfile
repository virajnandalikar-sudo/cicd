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
    }
    triggers {
        githubPush()
    }
}

