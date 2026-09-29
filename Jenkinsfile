pipeline {
    agent any

    stages {

        stage('Install Dependencies') {
            steps {
                bat 'git config --global --add safe.directory C:/src/flutter'
                bat 'flutter pub get'
            }
        }

        stage('Test') {
            steps {
                bat 'flutter test'
            }
        }

        stage('Build') {
            steps {
                bat 'flutter build web'
            }
        }

        stage('Archive Web Build') {
            steps {
                archiveArtifacts artifacts: 'build\\web\\**',
                                 fingerprint: true
            }
        }
    }
}