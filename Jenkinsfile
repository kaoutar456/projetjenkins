pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', 
                    branches: [[name: '*/main']], 
                    userRemoteConfigs: [[
                        url: 'https://github.com/kaoutar456/projetjenkins.git', 
                        credentialsId: '4dada6ed-77fe-4e4b-b800-89e8c924da77'
                    ]]
                ])
            }
        }

        stage('Build') {
            steps {
                echo "Building project..."
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying project..."
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}
