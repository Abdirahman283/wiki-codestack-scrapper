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
                    pip3 install requests
                    pip3 install beautifulsoup4
                    pip3 install lxml
                    pip3 install pandas
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
