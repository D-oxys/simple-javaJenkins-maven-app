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
        stage('Manual Approval') {
            steps {
                script {
                    // Menampilkan input message kepada pengguna
                    def userInput = input(
                        id: 'userInput', 
                        message: 'Lanjutkan ke tahap Deploy?', 
                        parameters: [choice(name: 'Pilihan', choices: 'Proceed\nAbort', description: 'Pilih tindakan')],
                        submitter: '', 
                        submitterParameter: 'APPROVE'
                    )
                    
                    // Mengecek tindakan yang dipilih oleh pengguna
                    if (userInput == 'Proceed') {
                        echo 'Melanjutkan ke tahap Deploy.'
                    } else {
                        currentBuild.result = 'ABORTED'
                        error('Eksekusi pipeline dihentikan oleh pengguna.')
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                sh './jenkins/scripts/deliver.sh'
            }
        }

        stage('Response') {
            steps {

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
