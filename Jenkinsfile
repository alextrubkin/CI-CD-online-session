pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        script {
          checkout scm
          def customImage = docker.build("${registry}:${env.BUILD_ID}")
        }

      }
    }

    stage('Publish') {
      steps {
        script {
          docker.withRegistry('', '9b5a9e7f-6bdf-425c-b640-1d7abd0f21ac') {
            docker.image("${registry}:${env.BUILD_ID}").push('latest')}
          }

        }
      }

    }
    environment {
      registry = 'alextrubkindocker/cicd_worshop'
    }
  }