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
            post {
                always {
                    junit '**/target/surefire-reports/*.xml'
                }
            }
        }

        stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
            }
        }
    }
}
