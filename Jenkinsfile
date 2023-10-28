pipeline {
    agent {
        label "jenkins-agent"
    }
    tools {
        jdk 'Java17'
        maven 'maven-3.9'
    }
    stages {
        stage("Cleanup Workspace") {
            steps {
                cleanWs()
            }
        }
        stage("Checkout from SCM") {
            steps {
               git branch: 'main', url: 'https://github.com/samir-mujanovic/java-maven-app' 
            }
        }
    }   
}