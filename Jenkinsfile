pipeline {
    agent any  // Utilisation d'un agent générique pour exécuter le pipeline

    environment {
        BUILD_DIR = "build"  // Répertoire où les fichiers peuvent être construits ou copiés
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
                    // Vous n'avez pas nécessairement besoin de build pour un projet statique.
                    // Vous pouvez effectuer des actions ici, comme vérifier les fichiers ou exécuter des tests.

                    echo "Building project..."

                    // Si vous avez des outils ou scripts spécifiques pour "compiler" ou traiter les fichiers,
                    // vous pouvez les ajouter ici (par exemple, en utilisant Node.js si vous avez un fichier package.json).
                    // Exemples :
                    // bat 'npm install'   // Pour installer les dépendances si vous utilisez Node.js
                    // bat 'npm run build' // Si vous avez un processus de build
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Étape de déploiement du projet
                    echo "Deploying project..."

                    // Par exemple, copiez les fichiers HTML, CSS, JS vers un répertoire de production
                    // Vous pouvez utiliser 'bat' pour exécuter des commandes batch sous Windows
                    bat '''
                    mkdir "%BUILD_DIR%"
                    copy *.html "%BUILD_DIR%"
                    copy *.css "%BUILD_DIR%"
                    copy *.js "%BUILD_DIR%"
                    '''

                    // Vous pouvez aussi ajouter un déploiement à un serveur ou un autre système ici
                    // Exemples : utiliser FTP, SFTP ou des outils de déploiement pour envoyer les fichiers
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
