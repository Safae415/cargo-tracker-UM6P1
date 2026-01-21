pipeline {
    agent any

    tools {
        maven 'Maven3' // Le nom que tu as défini dans Jenkins Global Tool Configuration
        jdk 'JDK 25'   // Assure-toi que le JDK est aussi configuré dans Jenkins
    }

    triggers {
        githubPush()   
    }

    stages {

        stage('Clone') {
            steps {
                git branch: 'develop', url: 'https://github.com/Safae415/cargo-tracker-UM6P1.git'
            }
        }

        stage('Build & Test with Coverage') {
            steps {
                // Maven est utilisé depuis Jenkins, pas besoin de PATH
                bat 'mvn clean verify'
            }
        }
      
    }

    post {
        success {
            echo 'Build et analyse terminés avec succès !'
        }
        failure {
            echo 'Échec du build ou des tests.'
        }
    }
}
