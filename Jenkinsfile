pipeline {
    agent any
 
    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/meghavathveeresh/onlinebookstore.git'
            }
        }
          stage('Build') {
            steps {
               bat 'mvn clean install'
            }
        }
          stage('Generate Artifacts') {
            steps {
               archiveArtifacts artifacts: 'target/*.war', followSymlinks: false
            }
        }
          stage('deploy tomcat server') {
            steps {
              deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'AMDN', path: '', url: 'http://localhost:8080/')], contextPath: 'meghavathveereshkumar', war: 'target/*.war'
            }
        }
    }
}    