pipeline {
    agent any

    stages {
        stage('Obtener el repositorio') {
            steps {
                git branch: 'main', url: 'git@github.com:alvalhor/openwebinars-curso-de-jenkins.git'
            }
        }
        stage('Construir la documetación') {
            steps {
                sh "doxygen"
            }
            
        }

        stage('Archivar la documentación') {
            steps {
                sh "zip documentation.zip -r html/*"
            }
        }
    }
    post {
        success {
            publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: 'html/', reportFiles: 'html/', reportName: 'Documentación', reportTitles: ''])
            archive "documentation.zip"
        }
    }
}
