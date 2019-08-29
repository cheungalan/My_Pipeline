pipeline {
  agent { 
    docker { 
      image 'webdevops/php-apache' 
      args '-p 8081:8081'
    } 
  }
  stages {
    stage('Build') {
      steps {
        sh 'php --version'
      }
    }
  stage('Test') {
      environment {
        CI = 'true'
      }
      steps {
        sh 'curl http://localhost:8081/test.php'
      }
    }
    stage('Deliver') {
      steps {
//        sh './jenkins/scripts/deliver.sh'
        input 'Finished using the web site? (Click "Proceed" to continue)'
//        sh './jenkins/scripts/kill.sh'
      }
    }
  }
}