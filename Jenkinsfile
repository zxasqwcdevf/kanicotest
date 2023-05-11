pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
		git branch: 'main', credentialsId: 'git', url: 'https://github.com/jhkim-09/test.git'
            }
        }
        stage('Build') {
            steps {
                sh "mvn -Dmaven.test.failure.ignore=true clean package"
            }
        }
        stage('Deploy') {
            steps {
		deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://192.168.56.12:8080')], contextPath: null, war: 'target/hello-world.war'
            }
        }
    }
}

