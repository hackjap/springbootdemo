pipeline {
    agent {
        kubernetes {
            yamlFile 'KubernetesPod.yaml'
        }   
    } 

    // 환경변수 
    environment {
        
        IMAGE = 'jangsp57/demo-springboot:v2'
        BRANCH = 'main'
        APP = 'AdminApi'
        DOCKER_REGISTRY = 'https://registry.dockerhub.com' 
        CREDENTIAL_REGISTRY = 'publicdocker'
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

    // stage('Clone repository') {
    //         steps {
    //             git branch: "master",
    //             credentialsId: 'github',
    //             url: 'https://github.com/hackjap/springdemo.git'
    //             sh 'ls -al'
    //             sh 'pwd'
    //         }
    //     }
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
                        docker login -u jangsp57  -p jspdk2919!
                        docker push ${IMAGE}
                        docker rmi ${IMAGE} -f 
                        '''
                }
            }
        }
    }   // End of stages 
} // End of pipeline
  