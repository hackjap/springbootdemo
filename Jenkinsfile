pipeline {
    agent any
    tool{
        maven 'Maven 3.6.3'
    }
    stages {
        stage('build') {
            steps {
                    sh "mvn clean package"
        }
    }
}

