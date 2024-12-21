pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                def scannerHome = tool 'sq_scanner'
                withSonarQubeEnv('sq1') {
                    sh "${scannerHome}/bin/sonar-scanner"
                }
            }
        }
    }
}
