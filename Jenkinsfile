pipeline {
    agent any

    stages {
        stage('Test') {
            steps {
                sh 'cd SampleWebApp mvn test'
            }
        }
        stage('Build') {
            steps {
                sh 'cd SampleWebApp && mvn clean package'
            }
        }
        
        stage('Deploy to Tomcat Web Server') {
            steps {
               deploy adapters: [tomcat9(credentialsId: 'tomcat_id', path: '', url: 'http://34.230.40.174:8080')], contextPath: 'webapp', war: '**/*.war'
            }
        }
    }
}
