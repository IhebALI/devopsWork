pipeline {
    agent any
     triggers {
        pollSCM('0 4 * * *')
    }
    stages {
       stage('checkout GIT') {
            steps {
                echo 'Pulling ...'
                git branch: 'master', url: 'https://github.com/IhebALI/devopsWork'
            }
        }
          stage('Compile') {
            steps {
                sh 'mvn compiler:compile '
            }
        }
         stage('Installing') {
            steps {
                sh 'mvn clean install'
            }
        }
       
     
       
         stage('Packaging') {
            steps {
                sh 'mvn package '
            }
        }
         stage('Tests') {
            steps {
                sh 'mvn test -DskipTests=false'
            }
        }
        stage('SONARQUBE') {
            steps {
                sh 'mvn sonar:sonar -Dsonar.login=3c4067e17e92431dab3da52651ca9a79f92de07d -Dsonar.ws.timeout=900000'
            }
        }
    }
}
