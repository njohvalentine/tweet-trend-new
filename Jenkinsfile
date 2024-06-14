
pipeline {
                                                         // Defines the entire pipeline script
    agent {
        label 'maven'  // Single quotes are preferred for labels
}                         // Specifies the agent (slave) with label 'maven' to run the pipeline

    stages {                                           // Defines different stages of the pipeline
        stage('build') {                               // Defines a stage named 'build'
            steps {                                       // Defines steps to be executed within the 'build' stage
                echo 'Building the application...'       // Prints a message to the console
                sh 'mvn clean deploy -Dmaven.test.skip-true' // Executes a shell command to build and deploy the application using Maven with the option to skip tests
                echo 'Build completed successfully!'     // Prints a message to the console
            }
        }

        stage('test') {                                  // Defines a stage named 'test'
            steps {                                       // Defines steps to be executed within the 'test' stage
                echo 'Running unit tests...'               // Prints a message to the console
                sh 'mvn surefire-report:report'            // Executes a shell command to run unit tests using Maven
                echo 'Unit tests completed!'                // Prints a message to the console
            }
        }

        stage('SonarQube analysis') {                   // Defines a stage named 'SonarQube analysis'
            environment {                                  // Defines environment variables for this stage
                scannerHome tool 'ttrend-sonarqube-scanner' // Sets the path to the SonarQube scanner tool
            }
            steps {                                       // Defines steps to be executed within the 'SonarQube analysis' stage
                script {                                    // Defines a script block to be executed
                    withSonarQubeEnv('sonarqube-server') { // Sets the SonarQube server name
                        sh "$(scannerHome)/bin/sonar-scanner\$" // Executes the SonarQube scanner to perform code analysis
                    }
                }
            }
        }
    }
}



