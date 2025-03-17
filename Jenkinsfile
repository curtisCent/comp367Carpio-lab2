pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "MAVEN3"
    }

    stages {
        stage("checkout"){
            steps{
                git branch: 'main', url: 'https://github.com/curtisCent/comp367Carpio-lab2'
            }
        }
        
        stage("Build maven project"){
            steps{
                sh 'mvn clean install'
            }
        }
        
        stage("Unit test"){
            steps{
                sh 'mvn test'
            }
        }
        
        stage("Docker build"){
            steps{
                script{
                    sh 'docker build -t lab3q1:latest -f .\\Dockerfile .'creden
                }
            }
        }
    }
}
