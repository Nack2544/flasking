pipeline {

  environment {
    registry = "nack2544/flask_app"
    registryCredentials = "docker"
    cluster_name = "skillstorm"
  }

  agent {
    node {
      label 'docker'
    }

  }
  stages {
    stage('Git') {
      steps {
        git(url: 'https://github.com/Nack2544/Flaskapp.git', branch: 'main')
      }
    }

    stage('Build Stage') {
      steps {
        script {
          dockerImage = docker.build(registry)
        }
      }
    }

    stage('Deployment Stage') {
      steps{
        script {
          docker.withRegistry('', registryCredentials) {
            dockerImage.push()
          }
        }
      }
    }

  }
}