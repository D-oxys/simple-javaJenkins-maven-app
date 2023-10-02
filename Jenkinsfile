pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Mengambil kode dari repositori Git
                git url: 'https://github.com/D-oxys/simple-javaJenkins-maven-app.git'
            }
        }

        stage('Build and Run') {
            steps {
                // Menjalankan skrip deliver.sh
                sh './jenkins/scripts/deliver.sh'
            }
        }

        stage('Test') {
            steps {
                // Menjalankan pengujian dengan Maven
                sh 'mvn test'
            }
        }

        stage('Post-Build Actions') {
            steps {
                echo 'berhasilsss...'
            }
        }
    }
}
