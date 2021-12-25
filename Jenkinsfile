pipeline {
    agent any
    stages {
        stage('build') {
            tool {
                maven 'Maven 3.6.3'
            }

            steps {
                 sh "mvn clean package"
            }
        }
    }
}   

