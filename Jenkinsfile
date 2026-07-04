pipeline {
    agent any

    stages {
        stage('checkout') {
            steps {
                // Get code from GitHub repository
                git 'https://github.com/bpolgardy/cicd-pipeline.git'

                sh 'echo "Checkout done."'
            }

        }
    }
}
