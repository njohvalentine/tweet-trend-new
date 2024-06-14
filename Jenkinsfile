pipeline {
  // Specify the agent label with Maven installed
  agent {
    label 'maven'
  }
  stages {
    stage('building the arifact') {
      steps {
        sh 'mvn clean deploy'
      }
    }
    stage('SonarQube analysis') {
    environment{ 
        scannerHome = tool 'ttrend-sonarqube-scanner';
    }
    steps{ 
    withSonarQubeEnv('ttrend-sonarqube-scanner') { // If you have configured more than one global server connection, you can specify its name
      sh "${scannerHome}/bin/sonar-scanner"
    }
    }
  }
  }
}