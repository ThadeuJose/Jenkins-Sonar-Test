pipeline {
    agent any

    tools {
        maven 'Maven'
    }

    stages{
        stage('SCM') {
            steps {
                git branch: 'master',  
                url: 'https://github.com/ThadeuJose/Jenkins-Sonar-Test.git'
            }            
        }

        stage('Mvn Package'){
            steps {
                sh 'mvn clean package'
            }            
        }

        stage('SonarQube analysis') {
            steps {
                withSonarQubeEnv('sonarqube') {

                sh 'mvn sonar:sonar -Dsonar.projectKey=gerenciadorprojeto-back -Dsonar.host.url=http://127.0.0.1:9000 -Dsonar.login=9e25125cd2c7897ba6ced991e52cc606f90cbe32'

                }
            }
        }
	}
}