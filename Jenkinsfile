pipeline {
    agent any
     triggers {
        pollSCM('0 4 * * *')
    }
    stages {
       stage('checkout GIT') {
            steps {
                echo 'Pulling ...'
                git branch: 'master', url: 'https://github.com/Medmalek98/DevOpsEsprit'
            }
        }
        
         stage('Maven Clean') {
            steps {
                sh 'mvn clean'
            }
        }
         stage('Maven Install') {
            steps {
                sh 'mvn install'
            }
        }
     
         stage('Compile') {
            steps {
                sh 'mvn compiler:compile '
            }
        }
         stage('Construction du livrable') {
            steps {
                sh 'mvn package '
            }
        }
         stage('Run Tests') {
            steps {
                sh 'mvn test -DskipTests=false'
            }
        }
        stage('Maven SONARQUBE') {
            steps {
                sh 'mvn sonar:sonar -Dsonar.login=3c4067e17e92431dab3da52651ca9a79f92de07d -Dsonar.ws.timeout=900000'
            }
        }
    }
}
