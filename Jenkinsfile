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
                 sh 'g++ hello.cpp -o hello'       
                                         
                }             
        }
        stage('Resumen') {
             steps { 
                 echo "Finalizado correctamente"
             }
        }
    }
}
