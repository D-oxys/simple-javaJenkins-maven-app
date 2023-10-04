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
                input message: 'Lanjutkan ke tahap Deploy?',
                      ok: 'Proceed',
                      submitter: 'any', 
                      parameters: [choice(
                            name: 'Pilihan', 
                            choices: 'Proceed\nAbort', 
                            description: 'Pilih tindakan'
                      )]
            }
        }

        stage('Deploy') {
            steps {
                sh './jenkins/scripts/deliver.sh'
                sleep(time: 60, unit: 'SECONDS')
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
