pipeline {
    agent any

    tools {
        // Add NodeJS in Jenkins Global Tools with this exact name "NodeJS"
        nodejs "NodeJS"
    }

    stages {
        stage('Checkout') {
            steps {
                echo "📥 Checking out code from GitHub..."
                git branch: 'main', url: 'https://github.com/kailashshaw090/jenkin-test.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                echo "📦 Installing dependencies..."
                sh 'npm install'
            }
        }

        stage('Lint') {
            steps {
                echo "🔎 Running Linter..."
                sh 'npm run lint || echo "Lint warnings found, continuing..."'
            }
        }

        stage('Test') {
            steps {
                echo "🧪 Running Tests..."
                sh 'npm test'
            }
        }

        stage('Build') {
            steps {
                echo "⚒️ Building project..."
                sh 'npm run build'
            }
        }

        stage('Deploy (Local Test)') {
            steps {
                echo "🚀 Deploy step (local testing only)"
                // Example: run your app locally
                // Adjust this if your app uses nodemon/pm2/etc.
                sh 'npm start &'
            }
        }
    }

    post {
        success {
            echo "✅ Build Successful!"
        }
        failure {
            echo "❌ Build Failed!"
        }
    }
}




