pipeline {
    agent any

    stages {
        
        stage('Build') {
            steps {
                sh '''
                   npm install
                   npm run build
                   '''
            }
        }

        stage('Test') {
            steps {
                sh 'CI=true npm test'
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

        stage('Scan Docker Image main for Vulnerabilities') {
            when {
                branch 'main'
            }
            steps {
                sh 'trivy image --exit-code 0 --severity HIGH,MEDIUM,LOW --no-progress nodemain:v1.0'
            }
        }

        stage('Scan Docker Image dev for Vulnerabilities') {
            when {
                branch 'dev'
            }
            steps {
                sh 'trivy image --exit-code 0 --severity HIGH,MEDIUM,LOW --no-progress nodedev:v1.0'
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
