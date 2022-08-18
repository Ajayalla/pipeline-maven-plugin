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
                dir("/var/lib/jenkins/workspace/New_demo/my-app/") {
                sh 'mvn -B -DskipTests clean package'
                }
                sh "fuser -k 8083/tcp"
               // sh "mvn package -Dmaven.test.skip=true"
            }
        }
    }
}
