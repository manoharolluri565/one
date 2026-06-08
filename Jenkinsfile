pipeline {
    agent any

    stages {

        stage('code-checkout') {
            steps {
                    deleteDir()
                    git 'https://github.com/Suresh5600/one.git'
            }
        }

        stage('code-build') {
            steps {
                    sh 'mvn clean package -DskipTests'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
            }
        }
    }
}
