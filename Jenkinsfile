pipeline {
  agent any
  stages {
    stage('Log versions') {
      parallel {
        stage('Log versions') {
          steps {
            sh '''mvn --version
git --version
java -version'''
          }
        }

        stage('POM existence') {
          steps {
            fileExists 'pom.xml'
          }
        }

      }
    }

    stage('Build with Maven') {
      steps {
        sh 'mvn compile test package'
      }
    }

    stage('Post-build') {
      steps {
        writeFile(file: 'status.txt', text: 'Success!')
      }
    }

  }
}