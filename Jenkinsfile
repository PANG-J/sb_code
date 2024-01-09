pipeline {
    agent any
    
    tools {
        maven 'my_maven'
    }
    environment {
        GITNAME = 'PANG-J' 
        GITEMAIL = 'rhkdgus1430@gmail.com' 
        GITWEBADD = 'https://github.com/PANG-J/sb_code.git'
        GITSSHADD = 'git@github.com:PANG-J/sb_code.git' 
        GITCREDENTIAL = 'git_cre' 
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
