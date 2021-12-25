pipeline {
    agent any
    stages {
        stage('build') {
            withMaven(maven: 'mvn'){
                    sh "mvn clean package"
            }
        }
    }
}

