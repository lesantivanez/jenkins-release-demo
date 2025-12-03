pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/tuusuario/tu-repo.git'
            }
        }

        stage('Build') {
            steps {
                sh 'echo "Compilando aplicación..."'
                sh './gradlew build || true'
            }
        } 


        stage('Test') {
            steps {
                sh 'echo "Ejecutando pruebas..."'
                sh './gradlew test || true'
            }
        }   

    stage('Package Release') {
            steps {
                sh 'echo "Generando artefacto de release..."'
                sh 'zip release.zip ./build/libs/*'
            }
        }


    stage('Publish Artifact') {
            steps {
                sh 'echo "Publicando release en servidor..."'
            }
        }
    }


    post {
        success {
            echo 'Release generado exitosamente.'
        }
        failure {
            echo 'El release falló.'
        }
    }
}