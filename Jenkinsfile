pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Mengambil kode dari repositori Git
                git url: 'https://github.com/D-oxys/simple-javaJenkins-maven-app.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Response') {
            steps {
               echo 'done ga bang??'
            }
        }
        
        stage('Final') {
            steps {
               echo 'donee'
            }
        }
    }
}
