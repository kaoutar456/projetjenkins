pipeline {
    agent any 

    stages {
        stage('Checkout') {
            steps {
                echo "Cloning repository..."
                checkout scm
            }
        }

        stage('Build') {
            steps {
                script {
                    echo "Building project..." 
                    // Copie des fichiers dans un dossier 'build'
                    bat 'mkdir build'
                    bat 'copy *.html build\\'
                    bat 'mkdir build\\css & copy css\\*.css build\\css\\'
                    bat 'mkdir build\\js & copy js\\*.js build\\js\\'
                    bat 'mkdir build\\img & copy img\\*.* build\\img\\'
                    bat 'mkdir build\\fonts & copy fonts\\*.* build\\fonts\\'
                    bat 'mkdir build\\slick & copy slick\\*.* build\\slick\\'
                }
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying project..."
                // Ajoutez votre logique de déploiement ici
            }
        }

        stage('Cleanup') {
            steps {
                cleanWs() 
            }
        }
    }
}
