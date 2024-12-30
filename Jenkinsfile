pipeline {
    agent any

    environment {
        BUILD_DIR = "build"  // Répertoire où les fichiers seront copiés
    }

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

                    bat """
                    REM Créer le répertoire 'build' s'il n'existe pas
                    if not exist ${BUILD_DIR} mkdir ${BUILD_DIR}

                    REM Minification et optimisation des fichiers CSS
                    echo Minifying CSS files...
                    if exist css\\*.css (
                        for %%i in (css\\*.css) do type %%i > ${BUILD_DIR}\\css\\%%~ni.min.css
                    )

                    REM Minification et optimisation des fichiers JS
                    echo Minifying JS files...
                    if exist js\\*.js (
                        for %%i in (js\\*.js) do type %%i > ${BUILD_DIR}\\js\\%%~ni.min.js
                    )

                    REM Copier les fichiers HTML dans le répertoire de build
                    echo Copying HTML files...
                    if exist *.html copy *.html ${BUILD_DIR}
                    """
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    echo "Deploying project..."

                    bat """
                    REM Copier les fichiers minifiés et ressources dans le répertoire final
                    if not exist ${BUILD_DIR}\\css mkdir ${BUILD_DIR}\\css
                    if exist ${BUILD_DIR}\\css\\*.min.css copy ${BUILD_DIR}\\css\\*.min.css ${BUILD_DIR}\\css

                    if not exist ${BUILD_DIR}\\js mkdir ${BUILD_DIR}\\js
                    if exist ${BUILD_DIR}\\js\\*.min.js copy ${BUILD_DIR}\\js\\*.min.js ${BUILD_DIR}\\js

                    if not exist ${BUILD_DIR}\\img mkdir ${BUILD_DIR}\\img
                    if exist img\\*.* copy img\\*.* ${BUILD_DIR}\\img

                    if not exist ${BUILD_DIR}\\fonts mkdir ${BUILD_DIR}\\fonts
                    if exist fonts\\*.* copy fonts\\*.* ${BUILD_DIR}\\fonts

                    echo Deployment complete. Files are ready in '${BUILD_DIR}'.
                    """
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
