pipeline {
    agent any 

    stages {
        stage('Clone') {
            steps {
                script {
                    // Cloner le dépôt Git
                    git url: 'https://github.com/meriem-achir/MyJavaApp.git', branch: 'main'
                }
            }
        }
        
        stage('Build') {
            steps {
                // Construire le projet avec Maven
                bat 'mvn clean package'
            }
        }
        
        stage('Test') {
            steps {
                // Exécuter les tests unitaires
                bat 'mvn test'
            }
        }

        stage('Run') {
            steps {
                // Exécuter l'application
                bat 'java -cp target/MyCalculatorProject-1.0-SNAPSHOT.jar com.example.Main'
            }
        }
    }

    post {
        always {
            // Toujours exécuter ce bloc, que le build réussisse ou échoue
            echo 'Cleaning up...'
        }

        success {
            echo 'Pipeline succeeded!'
        }

        failure {
            echo 'Pipeline failed!'
        }
    }
}
