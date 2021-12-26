pipeline {
    agent any
    podTemplate(
        label: label,
        container: [
            containerTemplate(name: "docker", image: "docker:latest",ttyEnabled:true,command:"cat"),
            containerTemplate(name: "kubectl", image: "lachlanevenson/k8s-kubectl", command: "cat", ttyEnabled: true) 
        ],
        // mount 
        volume: [
            hostPathVolume(hostPath:"/var/run/docker.sock", mountPath: "/var/run/docker/sock")
        ]
    )
    stages {
        // stage('mvn build') {
        //     steps {
        //         withMaven(globalMavenSettingsConfig: '2d1aa476-3d23-466f-9665-4a436e7db775', jdk: 'jdk-11', maven: 'maven 3.6.3', mavenSettingsConfig: 'd7d20abf-834c-4aef-bce6-463c51b5a917') {
            
        //             sh 'mvn clean package'
        //         }
        //     }
        // }
        stage("get source"){
            git branch: 'main', url: 'https://github.com/hackjap/springboot-demo.git'
        }
        
        stage('docker build') {
            steps {
                script {
                    container("docker"){
                        docker.withRegistry('https://registry.hub.docker.com', 'publicdocker'){
                            // def iamge = docker.build("jangsp57/demo-springboot:v2")
                            // image.push();
                            sh """
                                pwd
                                ls
                                docker build -t jangsp57/demo-springboot:v2 .
                                docker push jangsp57/demo-springboot:v2
                            """
                        }`
                    }
                }
            }
        }
    }
}
  