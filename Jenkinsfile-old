pipeline {
   agent any
    stages {
        stage('Checkout Code') {
            steps {
                 script{
                        dir("mavenproject")
                        {
                            git "https://github.com/kbindesh/mvn-lab-project.git"
                        }
                    }
                }
            }

        stage('Compile the code') {
            steps {
                sh 'mvn compile'
            }
        }
        stage('Package the app') {
            steps {
                script{
                if (params.ACTION == 'apply') {
                  sh "mvn package"
                } else {
                  sh "mvn package"
                }
            }
          }
        }
    }
  }
