pipeline {
    agent any

    stages {
        stage('Cloner et vérifier') {
            steps {
                echo 'Dépôt cloné avec succès !'
                sh 'ls -la'
            }
        }

        stage('Compiler avec Maven') {
            steps {
                echo 'Lancement de mvn package...'
                sh 'mvn clean package'
                echo 'Compilation terminée !'
            }
        }

        stage('Afficher les résultats') {
            steps {
                sh 'ls -la target/'
                archiveArtifacts artifacts: 'target/*.jar', allowEmptyArchive: true
            }
        }
    }

    post {
        success {
            echo '🎉 Pipeline CI réussi ! Tout est OK.'
        }
        failure {
            echo '❌ Échec du pipeline. Vérifiez les logs.'
        }
    }
}
