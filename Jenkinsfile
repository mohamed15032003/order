pipeline {
    agent any
    
    tools {
        maven 'Maven-3.9'
        jdk 'JDK-21'
    }
    
    stages {
        stage('1️⃣ Clone Repository') {
            steps {
                echo '📥 Clonage du repository Git...'
                git branch: 'main', url: 'https://github.com/mohamed15032003/order.git'
                echo '✅ Clonage terminé'
            }
        }
        
        stage('2️⃣ Build Project') {
            steps {
                echo '🔨 Compilation du projet avec Maven...'
                bat 'mvn clean compile'
                echo '✅ Compilation réussie'
            }
        }
        
        stage('3️⃣ Test & Package') {
            steps {
                echo '🧪 Tests et packaging...'
                bat 'mvn test package'
                echo '✅ Tests et packaging terminés'
            }
        }
    }
    
    post {
        success {
            echo '🎉 Pipeline exécuté avec succès !'
            archiveArtifacts artifacts: 'target/*.jar', allowEmptyArchive: true
        }
        failure {
            echo '❌ Le pipeline a échoué'
        }
    }
}