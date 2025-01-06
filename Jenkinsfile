pipeline {
  agent any
  stages {
    stage('Git Checkout') {
      steps {
        git(url: 'https://github.com/apohalo/cicd-pipeline.git', branch: 'main', poll: true, credentialsId: 'github_creds')
      }
    }

  }
}