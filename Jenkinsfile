pipeline {
    agent{
		docker{
			image 'composer:latest'
		}
	}
    stages {
        stage('Checkout SCM') {
            steps {
                git branch: 'main', credentialsId: '0c1c67ed-7cb0-4a61-a3bd-58a87497ae94', url: 'https://github.com/5partace/jenkinstest.git'
            }
        }
        stage('Build') {
            steps {
                sh 'composer install'
            }
        }
        stage('OWASP DependencyCheck') {
            steps {
                dependencyCheck additionalArguments: '--format HTML --format XML', odcInstallation: 'default'
            }
        }
        stage('Test') {
            steps {
                sh"tests --log-junit logs/unitreport.xml -c tests/phpunit.xml tests"
            }
        }
    }
    post {
        always{
            junit testResults: 'logs/unitreport.xml'
        }
        success {
            dependencyCheckPublisher pattern: 'dependency-check-report.xml'
        }
    }
}

