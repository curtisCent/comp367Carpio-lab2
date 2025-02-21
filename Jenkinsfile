pipeline {
    agent any

    triggers {
        pollSCM('H/2 * * * *') // Poll for changes every 2 minutes
    }

    stages {
        stage('POM existence') {
            parallel {
                stage('POM existence') {
                  steps {
                    fileExists 'pom.xml'
                  }
                }

                stage('Version check (fix)') {
                    steps {
                        bat 'mvn --version'
                    }
                }
            }
        }

        stage('Build with Maven (fix)') {
            steps {
                bat 'mvn compile test package'
            }
        }
    }

    post {
        success {
            echo 'Build succeeded!'
        }
        failure {
            echo 'Build failed!'
        }
        always {
            echo 'This message runs regardless of build outcome.'
        }
    }
}
