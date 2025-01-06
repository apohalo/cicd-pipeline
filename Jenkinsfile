pipeline {
  agent any
  stages {
    stage('Git') {
      steps {
        git(url: 'https://github.com/apohalo/cicd-pipeline.git', credentialsId: 'github_creds')
      }
    }

  }
}