#!groovy
pipeline {
  agent any
  options {
     skipStagesAfterUnstable()
     ansiColor('xterm')
  }
  environment {
    DOCKER_HOST = "tcp://${DOCKER_HOST}"
    IMAGES_DIR = 'library'
    REGISTRY_URL = "172.17.0.2:5000"
  }
  stages {
     stage('Build') {
        steps {
           sh '/usr/local/bin/ci build'
        }
     }
     stage('Push'){
       steps {
         sh '/usr/local/bin/ci push'
       }
     }
     stage('Cleanup') {
       steps {
         sh '/usr/local/bin/ci cleanup'
       }
     }
  }
}
