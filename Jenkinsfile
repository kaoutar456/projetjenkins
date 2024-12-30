pipeline {
    agent any

    environment {
        BUILD_DIR = "build"  // Répertoire où les fichiers seront construits ou copiés
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                script {
                    echo "Building project..."
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    echo "Deploying project..."
                    bat '''
                    REM Créer le répertoire build et ses sous-dossiers
                    mkdir "build" && mkdir "build\\css" && mkdir "build\\js" && mkdir "build\\img" && mkdir "build\\fonts" && mkdir "build\\slick"

                    REM Copier les fichiers HTML dans le répertoire 'build'
                    copy *.html "build"

                    REM Copier les fichiers CSS
                    copy css\\*.css "build\\css"

                    REM Copier les fichiers JS
                    copy js\\*.js "build\\js"

                    REM Copier les fichiers images
                    copy img\\*.* "build\\img"

                    REM Copier les fichiers de fonts
                    copy fonts\\*.* "build\\fonts"

                    REM Copier les fichiers du dossier slick
                    copy slick\\*.* "build\\slick"
                    '''
                }
            }
        }
    }

    post {
        always {
            echo "Cleaning up workspace..."
            cleanWs()
        }
    }
}
