pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'git@github.com:<your-username>/<your-repo>.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Build and Test') {
            steps {
                sh 'npm run build || echo "No build script"'
            }
        }
        stage('Deploy App') {
            steps {
                sh '''
                pkill node || true
                nohup node app.js > app.log 2>&1 &
                '''
            }
        }
    }
}
