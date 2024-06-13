pipeline {
  // Specify the agent label with Maven installed
  agent {
    label 'maven'
  }

  stages {
    stage('clone source code') {
      steps {
        git branch: 'main', url: 'https://github.com/njohvalentine/tweet-trend-new.git'
      }
    }
  }

  stages {
    stage('building the arifact') {
      steps {
        sh 'mvn clean deploy'
      }
    }
  }
}