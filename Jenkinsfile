pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git'
            }
        }

        stage('Check Flutter') {
            steps {
                bat 'flutter --version'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'flutter pub get'
            }
        }

        stage('Analyze') {
            steps {
                bat 'flutter analyze'
            }
        }

        stage('Test') {
            steps {
                bat 'flutter test'
            }
        }

        stage('Build APK') {
            steps {
                bat 'flutter build apk --release'
            }
        }
    }

    post {
        success {
            echo 'Flutter project built and tested successfully!'
        }

        failure {
            echo 'Flutter Jenkins pipeline failed!'
        }

        always {
            archiveArtifacts artifacts: 'build\\app\\outputs\\flutter-apk\\app-release.apk',
                             allowEmptyArchive: true
        }
    }
}