pipeline {
  agent any
  options {
    parallelsAlwaysFailFast()  
      }
  stages {

    stage('Parallel') {
      parallel {
        stage('docker-compose up') {
          steps {
            sh 'docker-compose up'
          }
        }
        stage('test') {
          steps {
            sh 'sleep 10'
            sh 'docker-compose down --remove-orphans'
          }
        }
      }
    }
  }

  post { 
    always {
      sh 'docker-compose down --remove-orphans'
    }
  }
}