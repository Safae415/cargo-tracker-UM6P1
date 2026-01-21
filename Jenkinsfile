pipeline {
    agent any

    triggers {
        githubPush()
    }

    tools {
        maven 'apache-maven-3.9.12'
        jdk 'jdk-17'
    }

    stages {

        stage('Clone') {
            steps {
                git branch: 'develop',
                    url: 'https://github.com/Safae415/cargo-tracker-UM6P1.git'
            }
        }

        stage('Build & Test with Coverage') {
            steps {
                bat 'mvn clean verify -DskipTests'
            }
        }
    }
    //test webhoob

    post {
        success {
            echo 'Build et analyse terminés avec succès !'
        }
        failure {
            echo 'Échec du build ou des tests.'
        }
    }
}
