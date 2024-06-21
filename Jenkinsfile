pipeline {
    agent { label 'Slave_node1'}
    tools {
        maven 'maven3.9.6' 
    }
    
    parameters {
        choice(name: 'Goal', choices: ['compile', 'test', 'package'], description: 'maven golas')
    }

    triggers {
        triggers { cron('* * * * *') }
    }

    stages {
        stage('source') {
            steps {
                git url: 'https://github.com/shashikjenkis/simple-java-maven-app.git',
                    branch: 'master'
            }
        }
        stage('packages') {
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

