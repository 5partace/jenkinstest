pipeline {
    agent any
    stages {
        stage('Checkout SCM') {
            steps {
                git branch: 'main', credentialsId: '0c1c67ed-7cb0-4a61-a3bd-58a87497ae94', url: 'https://github.com/5partace/jenkinstest'
            }
        }
        stage('OWASP DependencyCheck') {
            steps {
                dependencyCheck additionalArguments: '--format HTML --format XML', odcInstallation: 'default'
            }
        }
    }
    post {
        success {
            dependencyCheckPublisher pattern: 'dependency-check-report.xml'
        }
    }
}
