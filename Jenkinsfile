pipeline {
    agent any
    tools {
        maven 'Maven'  // Ensure Maven is installed in Jenkins
    }
    environment {
        DC_PATH = 'C:\\dependency-check\\bin\\dependency-check.bat'  // Change if using a different path
    }
    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/DILSHAD167/dependency-check.git'  // Update with your repo
            }
        }
        stage('Run OWASP Dependency-Check') {
            steps {
                bat "${DC_PATH} --project sample-project --scan . --format XML --out dependency-check-report.xml"
            }
        }
        stage('Publish OWASP Report') {
            steps {
                dependencyCheckPublisher pattern: '**/dependency-check-report.xml'
            }
        }
    }
}
