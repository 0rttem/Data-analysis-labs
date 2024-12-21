pipeline {
    agent any
    tools {
        maven 'Maven'
    }

    stages {
        stage('Git Checkout') {
            steps {
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/0rttem/Data-analysis-labs']])
                echo 'Git Checkout Completed'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('sq1') {
                    bat '''mvn clean verify sonar:sonar -Dsonar.projectKey=sonar -Dsonar.projectName='sonar' -Dsonar.host.url=http://localhost:9000''' //port 9000 is default for sonar
                    echo 'SonarQube Analysis Completed'
                }
            }
        }
    }
}
