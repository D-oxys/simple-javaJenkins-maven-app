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
