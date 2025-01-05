pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'script ./scripts/build.sh'
      }
    }

    stage('Test') {
      steps {
        sh 'script ./scripts/test.sh'
      }
    }

    stage('Docker build image') {
      steps {
        sh 'docker build -t cicdimage .'
      }
    }

    stage('Docker push') {
      steps {
        sh '''docker.withRegistry(\'https://registry.hub.docker.com\', \'docker_hub_creds_id\') 
{            
app.push("${env.BUILD_NUMBER}")
app.push("latest")
}
        
'''
      }
    }

  }
}