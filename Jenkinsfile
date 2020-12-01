pipeline {
    agent any
    stages {
        stage('Checkout SCM') {
            steps {
                git branch: 'main', credentialsId: 'bry', url: 'https://github.com/5partace/jenkinshook'
            }
        }
    }
}
