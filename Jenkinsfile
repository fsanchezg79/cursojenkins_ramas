pipeline {
    agent any

    stages {
        stage('Preparacion') {
            steps {
                echo 'Preparando el entorno...'
                sh 'ls'
            }
        }
        stage('Build') {
               steps { 
                 sh 'g++ main.cpp -o hello'       
                 sh './hello'                                      
                }             
        }
        stage('Resumen') {
             steps { 
                 echo "Finalizado correctamente"
                 archiveArtifacts artifacts: './hello'
             }
        }
    }
}
