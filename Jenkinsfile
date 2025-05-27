pipeline {
    agent any
    tools {
        maven 'MAVEN'
    }
    stages {
        stage('Checkout') {
            steps {
                // Récupérer le code depuis le dépôt Git
                checkout scm
            }
        }
        stage('Build Module') {
            steps {
                script {
                    // Construire le module Spring Boot
                    sh """
                        mvn clean install
                    """
                }
            }
        }
        
//        stage('SonarQube Analysis') {
//            steps {
//                // Nom du serveur configuré : SonarQubeServer
//                withSonarQubeEnv('SonarQubeServer') {
//                    sh '''
//                        mvn sonar:sonar \
//                            -Dsonar.java.binaries=. \
//                            -Dsonar.projectName=gr-conf-common-params \
//                            -Dsonar.projectKey=gr-conf-common-params
//                    '''
//                }
//            }
//        }

    }
    post {
        success {
            echo 'Module [gr-conf-common-params] installé avec succés..'
        }
        failure {
            echo 'Echec de l\'installation du module [gr-conf-common-params] !!'
        }
    }
}