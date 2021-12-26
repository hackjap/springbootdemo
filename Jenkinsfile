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

    // 환경변수 
    environment {
        IMAGE = 'jangsp57/demo-springboot:v2'
        BRANCH = 'main'

    }

    stages { 
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
                    sh '''
                        docker --version
                        ls
                        docker build -t ${IMAGE} .
                        docker images
                    '''
                }
            }
        }
    
        stage('Push Docker Image') {
            steps {
                container('docker'){
                    sh '''
                        docker login -u jangsp57 -p jspdk2919!
                        docker push ${IMAGE}'
                        docker rmi ${IMAGE}' -f 
                    '''
               
                }
            }
        }
    }   // End of stages 
} // End of pipeline
