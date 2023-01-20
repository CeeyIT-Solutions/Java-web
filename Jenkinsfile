pipeline {
    agent any
    tools {
        maven 'local_maven' 
    }
    stages {
        stage ('Build') {
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    stage ('Deploy') {
                        steps {
                            script {
                                deploy adapters: [tomcat9(path: '', url: 'http://35.178.136.139:8080/')], contextPath: null, war: '*/target/*.war'
                            }
                        }
                    }
                }
            }
        }
    }
}
