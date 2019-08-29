pipeline {
  agent { 
    docker { 
      image 'tutum/apache-php' 
      args '-p 8080:8080 -e ALLOW_OVERRIDE=true'
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
        sh 'php test.php'
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