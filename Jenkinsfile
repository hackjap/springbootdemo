pipeline {
    agent any
 tools {
    maven 'M3'
  }
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

