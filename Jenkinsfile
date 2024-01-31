pipeline {
    agent any

    stages {
        stage('Git Checkout') {
            steps {
                git 'https://github.com/uzair3399/CountryBank-Fullstack-App.git'
            }
        }
        
        stage('OWASP Dependency Check') {
            steps {
                 dependencyCheck additionalArguments: ' --scan ./ ', odcInstallation: 'DC'
                    dependencyCheckPublisher pattern: '**/dependency-check-report.xml'
            }
        }
        
        stage('trivy') {
            steps {
                 sh "trivy fs ."
            }
        }
        
         stage('Build & deploy') {
            steps {
                 sh " sudo docker-compose up -d"
            }
        }
    }
}
