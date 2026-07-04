pipeline {
    agent any

    stages {
        stage('test') {
            steps {
                // Display info about context

                sh '''
                   git branch --show-current
                   whoami
                   pwd
                   ls -la
                '''
            }

        }
    }
}
