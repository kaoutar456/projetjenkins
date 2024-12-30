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
                    REM Créer le répertoire "build" s'il n'existe pas
                    if not exist "%BUILD_DIR%" mkdir "%BUILD_DIR%"

                    REM Copier les fichiers HTML dans le répertoire 'build'
                    copy *.html "%BUILD_DIR%"

                    REM Copier les fichiers CSS depuis le dossier 'css' vers 'build'
                    if exist "css\\*" copy css\\*.css "%BUILD_DIR%\\css"

                    REM Copier les fichiers JS depuis le dossier 'js' vers 'build'
                    if exist "js\\*" copy js\\*.js "%BUILD_DIR%\\js"

                    REM Copier les fichiers images depuis le dossier 'img' vers 'build'
                    if exist "img\\*" copy img\\*.* "%BUILD_DIR%\\img"

                    REM Copier les fichiers de fonts depuis le dossier 'fonts' vers 'build'
                    if exist "fonts\\*" copy fonts\\*.* "%BUILD_DIR%\\fonts"

                    REM Copier les fichiers depuis le dossier 'slick' vers 'build'
                    if exist "slick\\*" copy slick\\*.* "%BUILD_DIR%\\slick"
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
