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
                   '''
            }
        }

        stage('Docker build main') {
            when {
                branch 'main'
            }
            steps {
                sh '''
		   echo "building nodemain:v1.0..."
                   docker build -t nodemain:v1.0 .
                   '''
            }
        }

        stage('Docker build dev') {
            when {
                branch 'dev'
            }
            steps {
                sh '''
                   echo "building nodedev:v1.0..."
                   docker build -t nodedev:v1.0 .
                   '''
            }
        }

        stage('Deploy main') {
            when {
                branch 'main'
            }
            steps {
                sh '''
                   echo "deploying nodemain:v1.0..."
                   docker run -d --name main-container -p 3000:3000 nodemain:v1.0
                   '''
            }
        }

        stage('Deploy dev') {
            when {
                branch 'dev'
            }
            steps {
                sh '''
                   echo "deploying nodedev:v1.0..."
                   docker run -d --name dev-container -p 3001:3000 nodedev:v1.0
                   '''
            }
        }

    }
}
