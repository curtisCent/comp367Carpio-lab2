pipeline {
  agent any
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

    stage('Post-build') {
      steps {
        writeFile(file: 'status.txt', text: 'Success!')
      }
    }

  }
}