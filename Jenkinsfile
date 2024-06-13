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
  }
}