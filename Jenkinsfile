pipeline {
    agent any
    stages {
        // stage('mvn build') {
        //     steps {
        //         withMaven(globalMavenSettingsConfig: '2d1aa476-3d23-466f-9665-4a436e7db775', jdk: 'jdk-11', maven: 'maven 3.6.3', mavenSettingsConfig: 'd7d20abf-834c-4aef-bce6-463c51b5a917') {
            
        //             sh 'mvn clean package'
        //         }
        //     }
        // }
        stage('docker build') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'publicdocker')
                    iamge = docker.build("jangsp57/demo-springboot:v2")
                    image.push();
                }
            }
        }
    }
}
