pipeline {
    agent any
    tools {
        maven 'Maven'
    }
    stages {
        stage("build") {
            steps {
                snDevOpsStep()
                snDevOpsChange()
                echo "Building" 
                sh "mvn clean install -DskipTests=true"
            }
        }

        stage('test') {
            steps {
                snDevOpsStep()
                snDevOpsChange()
                echo "Unit Test"
                sh "mvn test"
            }
            post {
                always {
                    junit '**/target/surefire-reports/*.xml' 
                }
          }
        }
        
        stage("deploy") {
            steps{
                snDevOpsStep ()
                echo "deploy in UAT"
                snDevOpsChange()
            }
        }
    }
}