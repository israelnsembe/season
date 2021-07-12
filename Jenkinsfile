pipeline {
    agent any
    tools {
        maven 'M2_HOME'
    }
    environment {
        registry = "izzylife10/mulunge"
        registryCredential = 'Docker_Registry'
    }
    stages {
        stage('Build'){
            steps {
                sh 'mvn clean'
                sh 'mvn install'
                sh 'mvn package'
            }
        }
        stage('Test'){
            steps {
                echo "test step"
                sh 'mvn test'
            }
        }
        stage('Docker'){
            steps {
                script {
                    docker.build registry + ":$BUILD_NUMBER"
                }
            }
        }
    }
}