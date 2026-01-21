pipeline {
    agent any

    triggers {
        githubPush()
    }

    stages {

        stage('Clone') {
            steps {
                git branch: 'develop', url: 'https://github.com/Safae415/cargo-tracker-UM6P1.git'
            }
        }

        stage('Check Maven') {
            steps {
                // Vérifie que Jenkins peut trouver Maven
                bat '"C:\\Program Files\\apache-maven-3.9.12\\bin\\mvn.cmd" -v'
            }
        }

        stage('Build & Test with Coverage') {
            steps {
                // Build et tests avec chemin complet vers Maven
                bat '"C:\\Program Files\\apache-maven-3.9.12\\bin\\mvn.cmd" clean verify'
            }
        }

    }

    post {
        success {
            echo 'Build et tests terminés avec succès !'
        }
        failure {
            echo 'Échec du build ou des tests.'
        }
    }
}
