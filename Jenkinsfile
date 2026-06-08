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
                sh 'cp target/*.war /opt/apache-tomcat-9.0.118/webapps/'
            }
        }
    }
}
