pipeline {
    agent any
    environment {
        PATH = "/opt/apache-maven-3.6.0/bin:$PATH"
    }
    stages {
        stage("clone code") {
            steps {
                git credentialsId: 'githublogin', branch: 'master', url: 'https://github.com/Ajayalla/pipeline-maven-plugin.git'
            }
        }
        stage("build code") {
            steps {
                sh "mvn clean build"
                sh "fuser -k 8083/tcp"
                sh "/var/lib/jenkins/workspace/Java-Project1/my-app/target/"
                sh "nohup java -jar gateway-0.0.1-SNAPSHOT.jar &"
               // sh "mvn package -Dmaven.test.skip=true"
            }
        }
    }
}
