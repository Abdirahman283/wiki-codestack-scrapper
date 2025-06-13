pipeline {
    agent any

    environment {
        NOM_PROJET = "Wikipedia-code-Scrapper"
    }

    stages {
        stage('Préparation') {
            steps {
                echo "Nom du projet : ${env.NOM_PROJET}"
                sh '''
                    echo "Installation des dependances..."
                    sudo apt update
                    sudo apt install -y python3 python3-pip
                    sudo apt install -y python3-requests python3-bs4 python3-lxml python3-pandas
                '''				
            }
        }

        stage('Scraping') {
            steps {
                sh 'python3 scrapper.py'
            }
        }

        stage('Archivage') {
            steps {
                echo "Stockage des donnees dans Jenkins"
                archiveArtifacts artifacts: '*.csv', fingerprint: true
                echo "Stockage des donnees reussi !"
            }
        }
    }
}
