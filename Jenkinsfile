pipeline {
    agent any

    stages {

        stage('code-checkout') {
            steps {
                    deleteDir()
                    git 'https://github.com/manoharolluri565/one.git'
            }
        }

        stage('code-build') {
            steps {
                    sh 'mvn clean package -DskipTests'
            }
        }
stage("Test") {
    withSonarQubeEnv("sonar") {
        sh "mvn sonar:sonar"
    }
}
        stage('Deploy to Tomcat') {
            steps {
           //     sh 'cp target/*.war /opt/apache-tomcat-9.0.118/webapps/'
                sshagent(['832957f9-ed9b-4575-84de-6705dcad8bcb'])  {
                sh 'scp -o StrictHostKeyChecking=no target/*.war root@98.130.120.8:/root/apache-tomcat-9.0.118/webapps/'
                }
            }
        }
    }
}
