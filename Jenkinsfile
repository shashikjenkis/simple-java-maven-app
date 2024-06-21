pipeline {
    agent { label 'Slave_node1'}
    tools {
        maven 'maven3.9.6' 
    }
    
    parameters {
        choice(name: 'Goal', choices: ['compile', 'test', 'package'], description: 'maven golas')
    }

    triggers {
        pollSCM('H/1 * * * *') // Polls the SCM every 5 minutes
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
                 sh "mvn ${params.Goal}"
            }
        }
         stage('archiveArtifacts') {
            steps {
                 archiveArtifacts artifacts: 'target/*.jar'
            }
        }
    }
    
    }

