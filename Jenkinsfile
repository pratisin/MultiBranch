pipeline {
    agent any
    options {
        skipStagesAfterUnstable()
    }
    tools {
        maven 'Maven'
    }

    stages {
        stage('Build') {
            steps {
                echo '------ Building ------'
                sh 'mvn -B -DskipTests clean compile'
            }
        }
        stage('Test') {
            steps {
                echo '------ Testing ------'
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                    
                    snDevOpsChange()
                }
                
            }
        }
        stage('Deploy') { 
            steps {
                echo '------ Deploying ------'
                //sh './jenkins/scripts/deliver.sh' 
            }
        }
    }
}
