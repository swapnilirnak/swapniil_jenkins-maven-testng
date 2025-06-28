pipeline {
    agent any

    tools {
        maven 'Maven 3.9'  // match the Maven name from Jenkins config
        jdk 'JDK21'        // match JDK name
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/swapnilirnak/swapniil_jenkins-maven-testng.git'
            }
        }

        stage('Build & Test') {

    steps {
        bat 'mvn clean test'
    }
}


            steps {
                sh 'mvn clean test'
            }
        }


        stage('Publish Test Results') {
            steps {
                junit '**/target/surefire-reports/*.xml'
            }
        }
    }

    post {
        always {
            mail to: 'swapnilirnaks@gmail.com',
                 subject: "Build #${env.BUILD_NUMBER} - ${currentBuild.currentResult}",
                 body: "Check Jenkins for details."
        }
    }
}
