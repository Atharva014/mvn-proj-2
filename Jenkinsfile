pipeline {

    // The agent name must match with the jenkins node name (Manage jenkins -> Nodes)
    agent {
        node {
            label 'Maven-build-node'
        }
    }

    // The tool name must match with the jenkins tools (global configuration) variable names
    tools {
        maven 'maven-3.9.8'
    }

    // Define environment variables
    environment {
        APP_NAME = "ATHARVA_APP"
        APP_ENV  = "PRODUCTION"
    }

    // Cleanup the jenkins workspace before building an Application
    stages {
        // Build the application code using Maven
        stage('Code Build stage') {
            steps {
                 sh 'mvn install -Dmaven.test.skip=true'
            }
        }
        
        stage('SonarQube Analysis') {
            environment {
                // Tool name must match with Jenkins Tools for Sonar Scanner - Manage Jenkins >> Tools
                scannerHome = tool 'sonar-scanner'
            }
            steps {
                // Env value must match with the Sonar Server Name - Manage Jenkins >> System
                withSonarQubeEnv('sonarqube-srv') {
                  sh "${scannerHome}/bin/sonar-scanner"
                }
            }
        }
    }
}
