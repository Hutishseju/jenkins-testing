pipeline {
    agent any

    environment {
        // Define Node.js version
        NODE_VERSION = '14.x'
    }

    stages {
        stage('Clone Repo') {
            steps {
                // Clone the repository with the correct branch
                git url: 'https://github.com/Hutishseju/jenkins-testing.git', branch: 'main'
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    // Install Node.js (using NodeSource for the specified version)
                    sh 'curl -sL https://deb.nodesource.com/setup_${NODE_VERSION} | sudo -E bash -'
                    sh 'sudo apt-get install -y nodejs'

                    // Install npm dependencies
                    sh 'npm install'
                }
            }
        }

        stage('Run Application') {
            steps {
                // Run the Node.js application
                script {
                    sh 'node server.js &'
                }
            }
        }

        stage('Verify Application') {
            steps {
                // Verify if the app is running by curling the localhost
                sh 'curl http://localhost:3000'
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
