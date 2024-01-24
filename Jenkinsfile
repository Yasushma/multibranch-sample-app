pipeline {
    agent any

    options {
        buildDiscarder(logRotator(numToKeepStr: '5'))
    }

    stages {
        stage('Build') {
            steps {
                script {
                    // Clean and build your Gradle project
                    sh './gradlew clean build --no-daemon'
                }
            }
        }
    }

    post {
        always {
            // Publish JUnit test results
            junit(
                allowEmptyResults: true,
                testResults: '**/build/test-results/test/*.xml'
            )
        }
    }
}
