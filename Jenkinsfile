pipeline {
  agent any
  stages {
    stage('Git Checkout') {
      steps {
        git(url: 'https://github.com/apohalo/cicd-pipeline.git', credentialsId: 'github_creds', branch: 'main', poll: true)
      }
    }

  }
}