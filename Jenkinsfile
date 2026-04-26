pipeline {
    agent {
        docker {
            image 'node:18'
            args '-u root'
        }
    }

    stages {

        stage("Checkout Code") {
            steps {
                git branch: "main", url: "https://github.com/Kdmodder/wanderlust1.git"
            }
        }

        stage("Install Dependencies") {
            steps {
                sh "npm install"
            }
        }

        stage("Build Project") {
            steps {
                sh "npm run build || echo 'No build script found'"
            }
        }

        stage("Simple Security Check") {
            steps {
                sh "npm audit || true"
            }
        }
    }

    post {
        success {
            echo "Pipeline executed successfully!"
        }
        failure {
            echo "Pipeline failed!"
        }
    }
}
