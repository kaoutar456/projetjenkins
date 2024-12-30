pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Récupérer le code du dépôt Git
                checkout scm
            }
        }

        stage('Build') {
            steps {
                script {
                    echo "Building project..." // Message d'état
                    // Créer un répertoire 'build' s'il n'existe pas
                    bat 'mkdir build'
                    
                    // Copier les fichiers HTML dans le répertoire 'build'
                    bat 'copy *.html build\\'
                    
                    // Copier les fichiers CSS
                    bat 'mkdir build\\css'
                    bat 'copy css\\*.css build\\css\\'
                    
                    // Copier les fichiers JS
                    bat 'mkdir build\\js'
                    bat 'copy js\\*.js build\\js\\'
                    
                    // Copier les fichiers d'images
                    bat 'mkdir build\\img'
                    bat 'copy img\\*.* build\\img\\'
                    
                    // Copier les fichiers de polices
                    bat 'mkdir build\\fonts'
                    bat 'copy fonts\\*.* build\\fonts\\'
                    
                    // Copier les fichiers depuis le dossier 'slick'
                    bat 'mkdir build\\slick'
                    bat 'copy slick\\*.* build\\slick\\'
                }
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying project..."
                // Ici, vous pourriez ajouter des étapes pour déployer le contenu du répertoire 'build'
            }
        }

        stage('Cleanup') {
            steps {
                cleanWs() // Nettoyer l'espace de travail
            }
        }
    }
}
