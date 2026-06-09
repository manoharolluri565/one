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

        stage('Deploy to Tomcat') {
            steps {
           //     sh 'cp target/*.war /opt/apache-tomcat-9.0.118/webapps/'
                sshagent(['4a030588-8826-4db7-8c30-2dceb9c941e2']) {
                sh 'scp -o StrictHostKeyChecking=no target/*.war root@98.130.120.8:/root/apache-tomcat-9.0.118/webapps/'
                }
            }
        }
    }
}
