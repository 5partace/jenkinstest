pipeline {
    agent any
    stages {
        stage('Checkout SCM') {
            steps {
                git branch: 'main', credentialsId: '10741db6-9908-4d13-ac4b-84ed37384886', url: 'https://github.com/5partace/jenkinstest.git'
            }
        }
    }
}
