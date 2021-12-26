pipeline {
    agent {
        kubernetes {
            yaml """
apiVersion: v1
kind: Pod
metadata:
  labels:
    some-label: pod
spec:
  containers:
  - name: maven-jdk8-node
    image: maven:3.8.4-openjdk-8-slim
    command:
    - cat
    tty: true
  - name: docker
    image: docker:latest 
    volumeMounts:
    - name: dockersock
      mountPath: "/var/run/docker.sock"
    command:
    - cat
    tty: true
  volumes:
  - name: dockersock
    hostPath:
      path: /var/run/docker.sock
  - name: hosts
    hostPath:
      path: /etc/hosts
"""
        }
    }
    stages {
        stage('Clone repository') {
            steps {
                git branch: "master",
                credentialsId: 'github',
                url: 'https://github.com/hackjap/springbootdemo.git'
                sh 'ls -al'
                sh 'pwd'
            }
        }
        
        // stage('Maven Build') {
        //     steps {
        //         container('maven-jdk-node'){
        //             sh 'mvn -v'
        //             sh "mvn -P dev -f ./AdminApi/pom.xml clean package"
        //             sh "ls -al ./AdminApi/target"
        //             sh "pwd"
        //         }
        //     }
        // }

        stage('Build Docker Image'){
            steps {
                container('docker'){
                    sh 'docker --version'
                    sh 'ls'
                    sh 'docker build -t jangsp57/demo-springboot:latest .'
                    sh 'docker images'
                }
            }
        }
        
        stage('Push Docker Image') {
            steps {
                container('docker'){
                    sh 'docker login -u jangsp57 -p jspdk2919!'
                    sh 'docker push jangsp57/demo-springboot:latest:'
                }
            }
        }
    }
}