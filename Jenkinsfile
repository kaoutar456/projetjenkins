pipeline {
    agent any  // Utilisation d'un agent générique pour exécuter le pipeline

    environment {
        BUILD_DIR = "build"  // Répertoire où les fichiers seront construits ou copiés
    }

    stages {
        stage('Checkout') {
            steps {
                // Clone le repository Git pour récupérer le code source
                checkout scm
            }
        }

        stage('Build') {
            steps {
                script {
                    // Vous pouvez ajouter des étapes spécifiques si vous avez des outils de build à exécuter
                    echo "Building project..."
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    echo "Deploying project..."
                    bat '''
                    mkdir "build"
                    
                    // Copier les fichiers HTML dans le répertoire 'build'
                    copy *.html "build"
                    
                    // Copier les fichiers CSS depuis le dossier 'css' vers 'build'
                    copy css\\*.css "build\\css"
                    
                    // Copier les fichiers JS depuis le dossier 'js' vers 'build'
                    copy js\\*.js "build\\js"
                    
                    // Copier les fichiers images depuis le dossier 'img' vers 'build'
                    copy img\\*.* "build\\img"
                    
                    // Copier les fichiers de fonts depuis le dossier 'fonts' vers 'build'
                    copy fonts\\*.* "build\\fonts"
                    
                    // Copier les fichiers depuis le dossier 'slick' vers 'build'
                    copy slick\\*.* "build\\slick"
                    '''
                }
            }
        }
    }

    post {
        always {
            // Nettoyer l'espace de travail après chaque build
            cleanWs()
        }
    }
}
