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
                bat 'mvn clean install'
            }
        }
        
        stage("Unit test"){
            steps{
                bat 'mvn test'
            }
        }
        
        stage("Docker build"){
            steps{
                script{
                    bat 'docker build -t lab3q1:latest -f .\\Dockerfile .'
                }
            }
        }
    }
}
