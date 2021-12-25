pipeline {
    agent any
    stages {
        stage('Hello') {
            steps {
                withMaven(maven: 'mvn'){
                     sh "mvn clean package"
                }
            }
        }
    }
}

