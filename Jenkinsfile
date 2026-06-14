pipeline {
    agent any

    stages {

        stage('Code Checkout') {
            steps {
                deleteDir()
                git 'https://github.com/manoharolluri565/one.git'
            }
        }

        stage('Code Build') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('sonar') {
                    sh 'mvn sonar:sonar'
                }
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                sshagent(['832957f9-ed9b-4575-84de-6705dcad8bcb']) {
                    sh '''
                        scp -o StrictHostKeyChecking=no \
                        target/*.war \
                        root@98.130.120.8:/root/apache-tomcat-9.0.118/webapps/
                    '''
                }
            }
        }
    }
}
