pipeline {
    agent any
    
    tools {
        maven 'my_maven'
    }
    environment {
        GITNAME = 'PANG-J' #자신의 깃허브 계정
        GITEMAIL = 'rhkdgus1430@gmail.com' #자신의 이메일계정
        GITWEBADD = 'https://github.com/PANG-J/sb_code.git'
        GITSSHADD = 'git@github.com:PANG-J/sb_code.git' #나중에 SSH를 통해 푸쉴르 하기위해 필요
        GITCREDENTIAL = 'git_cre'  #젠킨스 credential에서 생성 했던것을 입력.
    }
    
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
