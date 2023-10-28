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
        stage("Build Application") {
            steps {
               sh "mvn clean package"
            }
        }
        stage("Test Application") {
            steps {
               sh "mvn test"
            }
        }
        stage("Sonarqube Analysis") {
            steps {
               withSonarQubeEnv(credentialsId: 'jenkins-sonarqube-token') {
                    sh "mvn sonar:sonar"
               }
            }
        }
    }   
}