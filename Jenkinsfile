pipeline {
    agent any
    
    tools {
        maven 'my maven'
    }
    environment {
        GITNAME = 'PANG-J' 
        GITEMAIL = 'rhkdgus1430@gmail.com' 
        GITWEBADD = 'https://github.com/PANG-J/sb_code.git'
        GITSSHADD = 'git@github.com:PANG-J/sb_code.git' 
        GITCREDENTIAL = 'git_cre' 
        
        DOCKERHUB = 'pang916/spring'
        DOCKERHUBCREDENTIAL = 'docker_cri'
    }
    
    stages {
        stage('Checkout Github') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [],
                userRemoteConfigs: [[credentialsId: GITCREDENTIAL, url: GITWEBADD]]])
            }
        
            post {
        
                failure {
                    echo 'Repository clone failure'
                }
                success {
                    echo 'Repository clone success'
                }
            }
        }
        
        
        stage('code build') {
            steps {
                sh "mvn clean package"
            }
        }
        
        stage('image build') {
            steps {
               sh "docker build -t ${DOCKERHUB}:${currentBuild.number} ."
               sh "docker build -t ${DOCKERHUB}:latest ."
               //currentBuild.number jenkins의 빌드 넘버
               //pang916/spring:1 같은 형태로 빌드가 될 것이다.
            }
        }
    
        stage('image push') {
            steps {
               sh "docker push ${DOCKERHUB}:${currentBuild.number}"
               sh "docker push ${DOCKERHUB}:latest"
            }
            post {
                failure (
                    echo 'docker image push failure'
                    sh "docker image rm -f ${DOCKERHUB}:${currentBuild.number}"
                    sh "docker image rm -f $(DOCKERHUB}:latest"
                )
                success (
                    echo 'docker image push success'
                    sh "docker image rm -f ${DOCKERHUB}:${currentBuild.number}"
                    sh "docker image rm -f $(DOCKERHUB}:latest"
        }
    }
}