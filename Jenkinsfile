pipeline {
    agent any  // Utiliser n'importe quel agent

    stages {
        stage('Checkout') {
            steps {
                // Récupérer le code source
                git 'https://github.com/kaoutar456/projetjenkins.git'
            }
        }

        stage('Build') {
            steps {
                // Étapes de construction (ajoutez ce qui est nécessaire pour votre projet)
                echo 'Building the project...'
                // Par exemple, vous pourriez lancer une commande pour construire votre projet
            }
        }
        
        stage('Test') {
            steps {
                // Étapes de tests (si nécessaire)
                echo 'Running tests...'
                // Commands to run tests would go here
            }
        }

        stage('Deploy') {
            steps {
                // Étapes de déploiement (ajoutez ce qui est nécessaire pour votre projet)
                echo 'Deploying the project...'
                // Example: you could copy files to a web server directory
            }
        }

        stage('Cleanup') {
            steps {
                echo 'Cleaning up...'
                // Clean up steps if necessary
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
