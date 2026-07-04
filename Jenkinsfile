pipeline {
    agent any

    stages {
        stage('test') {
            when {
                branch 'main'
            }
            steps {
                // Display info about context

                sh '''
                   echo "BRANCH_NAME=$BRANCH_NAME"
                   echo "JOB_NAME=$JOB_NAME"
                   echo "WORKSPACE=$WORKSPACE"
                   '''
            }
            when {
                branch 'dev'
            }
            steps {
                // Display info about context

                sh '''
                   echo "BRANCH_NAME=$BRANCH_NAME"
                   echo "JOB_NAME=$JOB_NAME"
                   echo "WORKSPACE=$WORKSPACE"
                   '''
            }
        }
    }
}
