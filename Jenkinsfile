pipeline {
    agent {
        node {
            label 'built-in'
            customWorkspace '/mnt/war'
        }
    }

    stages {

        stage('SCM') {
            steps {
                sh '''
                rm -rf project
                git clone https://github.com/Hrishikeshkul/projectDF.git
                '''
            }
        }

        stage('BUILD') {
            steps {
                sh '''
                cd /mnt/war/project
                mvn clean package
                '''
            }
        }
      stage('DEPLOY ON SLAVE') {
            agent {
                node {
                    label 'slave1'
                    customWorkspace '/mnt/jenkins-slave1'
                }
            }
       steps {
                sh '''
                docker build -t testing .
        
