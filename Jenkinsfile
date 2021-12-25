pipeline {
    agent any
    stages {
        stage('build') {
            tools {
                maven 'Maven 3.6.3'
            }

            steps {
                 sh "mvn clean package"
            }
        }
    }
}   

