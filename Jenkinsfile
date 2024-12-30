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
                    REM Afficher le contenu du répertoire avant d'exécuter les opérations
                    echo "Affichage du répertoire courant :"
                    echo %cd%

                    REM Afficher la liste des fichiers et répertoires du dépôt
                    dir

                    REM Créer le répertoire "build" s'il n'existe pas
                    if not exist "%BUILD_DIR%" (
                        echo "Répertoire '%BUILD_DIR%' n'existe pas, création..."
                        mkdir "%BUILD_DIR%"
                    ) else (
                        echo "Répertoire '%BUILD_DIR%' existe déjà."
                    )

                    REM Vérification de l'existence des fichiers HTML
                    echo "Vérification des fichiers HTML"
                    if exist "*.html" (
                        echo "Fichiers HTML trouvés"
                    ) else (
                        echo "Aucun fichier HTML trouvé"
                    )

                    REM Copier les fichiers HTML dans le répertoire 'build'
                    if exist "*.html" (
                        echo "Copie des fichiers HTML dans '%BUILD_DIR%'..."
                        copy *.html "%BUILD_DIR%"
                    )

                    REM Copier les fichiers CSS depuis le dossier 'css' vers 'build'
                    if exist "css\\*" (
                        echo "Copie des fichiers CSS dans '%BUILD_DIR%\\css'..."
                        copy css\\*.css "%BUILD_DIR%\\css"
                    ) else (
                        echo "Aucun fichier CSS trouvé"
                    )

                    REM Copier les fichiers JS depuis le dossier 'js' vers 'build'
                    if exist "js\\*" (
                        echo "Copie des fichiers JS dans '%BUILD_DIR%\\js'..."
                        copy js\\*.js "%BUILD_DIR%\\js"
                    ) else (
                        echo "Aucun fichier JS trouvé"
                    )

                    REM Copier les fichiers images depuis le dossier 'img' vers 'build'
                    if exist "img\\*" (
                        echo "Copie des fichiers images dans '%BUILD_DIR%\\img'..."
                        copy img\\*.* "%BUILD_DIR%\\img"
                    ) else (
                        echo "Aucun fichier image trouvé"
                    )

                    REM Copier les fichiers de fonts depuis le dossier 'fonts' vers 'build'
                    if exist "fonts\\*" (
                        echo "Copie des fichiers fonts dans '%BUILD_DIR%\\fonts'..."
                        copy fonts\\*.* "%BUILD_DIR%\\fonts"
                    ) else (
                        echo "Aucun fichier de fonts trouvé"
                    )

                    REM Copier les fichiers depuis le dossier 'slick' vers 'build'
                    if exist "slick\\*" (
                        echo "Copie des fichiers slick dans '%BUILD_DIR%\\slick'..."
                        copy slick\\*.* "%BUILD_DIR%\\slick"
                    ) else (
                        echo "Aucun fichier slick trouvé"
                    )
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
