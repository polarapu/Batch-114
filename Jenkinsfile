pipeline {
    agent any
    tools { 
        maven 'Maven'  
    }
    stages {
        stage('SCM') {
            steps {
                echo 'Cloning git repo from git-hub'
                git credentialsId: '0e1fcd62-64fb-489a-9431-d4b84fa49e97', url: 'https://github.com/polarapu/maven-project1.git'
            }
        }
        stage('Build') {
            steps {
                echo 'Maven build using mvn clean install command'
                sh 'mvn clean install'
            }
        }
        stage('Deploy-stage') {
            steps {
                echo 'Deploying into tomcat app.'
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'e008ef50-eea9-48c3-b974-4bbf8962a61a', path: '', url: 'http://192.168.32.128:8081/')], contextPath: 'devops114.war', war: '**/*.war'
            }
        }
    }
}
