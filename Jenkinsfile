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

    stage('Docker image') {
      steps {
        script {
          script {
            docker.build("${env.IMAGE_NAME}:${env.BUILD_NUMBER}")
          }
        }

      }
    }

    stage('Docker Push') {
      steps {
        script {
          script {
            docker.withRegistry('https://registry.hub.docker.com', 'docker_hub_creds_id') {
              def app = docker.image("${env.IMAGE_NAME}:${env.BUILD_NUMBER}")
              app.push("${env.BUILD_NUMBER}")
              app.push("latest")}
            }


          }

        }
      }

    }
  }