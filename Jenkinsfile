pipeline {
  agent { 
    docker { 
      image 'tutum/apache-php' 
      args '-p 80:80'
    } 
  }
  stages {
    stage('Build') {
      steps {
        sh 'php --version'
        sh 'service apache-php start'
      }
    }
  stage('Test') {
      environment {
        CI = 'true'
      }
      steps {
        sh 'curl http://localhost/test.php'
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