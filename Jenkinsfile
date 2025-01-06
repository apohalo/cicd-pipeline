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
        sh '''withDockerRegistry(credentialsId: \'docker_hub_creds_id\', url: \'https://index.docker.io/v1/\')
{            
docker.image(\'cicdimage\').push ("${env.BUILD_NUMBER}")
docker.image(\'cicdimage\').push ("latest")
}
        
'''
      }
    }

  }
}