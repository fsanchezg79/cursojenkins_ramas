pipeline {
    agent any
 
    environment {
        BUILD_DIR = "build"
        BIN_NAME = "hello.exe"
    }
 
    stages {
 
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
 
        stage('Lint (cppcheck)') {
            steps {
                echo 'Running cppcheck...'
                bat """
                if not exist reports mkdir reports
                cppcheck --enable=all --inconclusive --quiet src 2> reports/cppcheck.txt
                """
            }
        }
 
        stage('Compile (Windows)') {
            steps {
                echo 'Compiling for Windows...'
                bat """
                if not exist %BUILD_DIR% mkdir %BUILD_DIR%
                gcc src\\hello.c -o %BUILD_DIR%\\%BIN_NAME%
                """
            }
        }
 
        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: 'build/*.exe, reports/*.txt', fingerprint: true
            }
        }
    }
 
    post {
        always {
            echo 'Pipeline finished'
        }
        success {
            echo 'Build SUCCESS'
        }
        failure {
            echo 'Build FAILURE'
        }
    }
}
