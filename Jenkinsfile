pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        git branch: 'main', url: 'https://github.com/Christophe-Shumbusho/Group2-API-testing-framework.git'
      }
    }

    stage('Install Dependencies') {
      steps {
        bat 'npm install -g newman newman-reporter-htmlextra'
      }
    }

    stage('Run Tests') {
      steps {
        bat 'newman run userManagementUpdated.json -e Staging.env.postman_environment.json -d loginCredentialJenkins.csv -r htmlextra --reporter-htmlextra-export newman-report.html'
      }
    }

    stage('Archive Report') {
      steps {
        archiveArtifacts artifacts: 'newman-report.html', fingerprint: true
      }
    }
  }
}
