pipeline {
    agent any
    stages {
        stage('Clone Repository') { steps { checkout scm } }
        stage('Build with Maven') { steps { sh 'mvn clean compile' } }
        stage('Run JUnit Tests') { steps { sh 'mvn test' } }
        stage('Package') { steps { sh 'mvn package -DskipTests' } }
        stage('Docker Build') { steps { sh 'docker build -t library-system:latest .' } }
        stage('Docker Run') { steps { sh 'docker run --name lib-app library-system:latest' } }
    }
}
