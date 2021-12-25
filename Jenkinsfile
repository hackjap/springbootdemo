pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                 withMaven(globalMavenSettingsConfig: '2d1aa476-3d23-466f-9665-4a436e7db775', jdk: 'jdk-11', maven: 'maven 3.6.3', mavenSettingsConfig: 'd7d20abf-834c-4aef-bce6-463c51b5a917') {
                     sh "pwd"
                     sh "cat Jenkinsfile"
                     sh "mvn clean package"
                }
            }
        }
    }
}   

