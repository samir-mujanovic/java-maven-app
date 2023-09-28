pipeline {
    agent any
    stages {
        stage('test') {
            steps {
                script {
                    echo "Testing the application..."
                }
            }
        }
        stage('build') {
            steps {
                script {
                    echo "Building the application..."
                }
            }
        }
        stage('deploy') {
            steps {
                script {
                    def dockerCmd = 'docker run -p 3080:3080 -d xhawk1337/demo-app:1.0'
                    sshagent(['aws-key']) {
                        sh "ssh -o StrictHostKeyChecking=no ec2-user@3.127.218.231 ${dockerCmd}"
                    }
                }
            }
        }
    }
}
