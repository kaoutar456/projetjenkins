pipeline {
    agent any 

    environment {
        BUILD_DIR = "build"
    }

    stages {
        stage('Checkout') {
            steps {
                echo "Checking out code..."
                checkout scm
            }
        }

        stage('Build') {
            steps {
                script {
                    echo "Building project..." 
                    // Ici, vous pouvez ajouter des étapes de construction spécifiques
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    echo "Deploying project..."
                    bat '''
                    mkdir "build"
                    copy *.html "build"
                    mkdir build\\css & copy css\\*.css "build\\css"
                    mkdir build\\js & copy js\\*.js "build\\js"
                    mkdir build\\img & copy img\\*.* "build\\img"
                    mkdir build\\fonts & copy fonts\\*.* "build\\fonts"
                    mkdir build\\slick & copy slick\\*.* "build\\slick"
                    '''
                }
            }
        }
    }

    post {
        always {
            script {
                echo "Cleaning workspace..."
                cleanWs()
            }
        }
    }
}
