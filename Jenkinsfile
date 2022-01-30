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

                sh 'mvn sonar:sonar -Dsonar.projectKey=TestJenkins -Dsonar.host.url=http://java-sonar-jenkins-teste-sonarqube-1:9000 -Dsonar.login=9763b1bd1f641f1b2a5e082a27df95ab2fd6ace2'

                }
            }
        }
	}
}