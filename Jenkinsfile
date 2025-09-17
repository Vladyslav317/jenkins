pipeline {
    agent any

    tools {
        nodejs "NodeJS" // The name you configured
    }

    stages {
        stage('Install Node.js') {
              steps {
                  sh '''
                    curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
                    sudo apt-get install -y nodejs
                    node -v
                    npm -v
                  '''
              }
          }

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Vladyslav317/jenkins.git'
            }
        }

        stage('Install') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Test') {
            steps {
                sh 'npm run test'
            }
        }
    }
}
