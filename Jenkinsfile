pipeline {
    agent { label 'Slave_node1'}
    tools {
        maven 'maven3.9.6' 
    }
    stages {
        stage('source') {
            steps {
                git url: 'https://github.com/shashikjenkis/simple-java-maven-app.git',
                    branch: 'master'
            }
        }
        stage('package') {
            steps {
                 sh 'mvn package'
            }
        }
    }
    
    }

