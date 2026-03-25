pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        git 'https://github.com/your-username/postman-newman-ci.git'
      }
    }

    stage('Install Dependencies') {
      steps {
        bat 'npm install -g newman newman-reporter-htmlextra'
      }
    }

    stage('Run Tests') {
      steps {
        bat 'newman run userManagement_API.json -e Staging.env.postman_environment.json -r htmlextra --reporter-htmlextra-export newman-report.html'
      }
    }

    stage('Archive Report') {
      steps {
        archiveArtifacts artifacts: 'newman-report.html', fingerprint: true
      }
    }
  }
}
