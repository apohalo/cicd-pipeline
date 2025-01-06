pipeline {
  agent any
  stages {
    stage('Git Checkout') {
      steps {
        git(url: 'https://github.com/apohalo/cicd-pipeline.git', branch: 'main', poll: true, credentialsId: 'github_creds')
      }
    }

    stage('Build') {
      steps {
        sh '''chmod +x scripts/build.sh
script ./scripts/build.sh'''
      }
    }

    stage('Test') {
      steps {
        sh '''chmod +x scripts/test.sh
script ./scripts/test.sh'''
      }
    }

    stage('Docker Image') {
      steps {
        echo 'Building docker image'
        sh 'docker build -t cicd .'
      }
    }

    stage('Docker Push') {
      steps {
        sh '''docker image tag cicd:latest aigulsadykova/test-jenkins-pipeline:v2
docker image push aigulsadykova/test-jenkins-pipeline:v2'''
      }
    }

  }
}