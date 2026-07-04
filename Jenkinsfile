pipeline {
    agent any

    stages {
        stage('test') {
            steps {
                // Display info about context

                sh '''
                   echo "BRANCH_NAME=$BRANCH_NAME"
                   echo "JOB_NAME=$JOB_NAME"
                   echo "WORKSPACE=$WORKSPACE"
                   whoami
                   pwd
                   ls -la
                   '''
            }

        }
    }
}
