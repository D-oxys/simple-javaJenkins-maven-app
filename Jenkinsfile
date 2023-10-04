pipeline {
    agent any
    stages {
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
            def userInput = input(
                id: 'userInput', 
                message: 'Lanjutkan ke tahap Deploy?', 
                parameters: [choice(
                    name: 'Pilihan', 
                    choices: 'Proceed\nAbort', 
                    description: 'Pilih tindakan'
                )],
                submitter: 'any', 
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
