pipeline {
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                sh 'docker build -t zularbine/devops001 .'
            }
        }
    }
}