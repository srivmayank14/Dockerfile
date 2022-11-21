pipeline {
    agent { dockerfile true }
    stages {
        stage('Test') {
            steps {
                sh 'docker build -it Dockerfile'
                sh 'nginx --version'
            }
        }
    }
}
