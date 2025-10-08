pipeline {
    agent any

    environment {
        PYTHON_PATH = 'C:\\Users\\NANDKISHOR\\AppData\\Local\\Programs\\Python\\Python311\\python.exe'
    }

    stages {
        stage('Pull Code') {
            steps {
                echo 'Pulling latest code from GitHub'
                git branch: 'main', url: 'https://github.com/Nandkishor-Jagtap/flask-todo-app.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                echo 'Installing Python dependencies'
                bat "${env.PYTHON_PATH} -m pip install --upgrade pip"
                bat "${env.PYTHON_PATH} -m pip install -r requirements.txt"
            }
        }

        stage('Run Flask App') {
            steps {
                echo 'Starting Flask App'
                // Kill previous Python process if running
                bat 'taskkill /F /IM python.exe /T || exit 0'
                // Start Flask app in background
                bat "start cmd /c \"${env.PYTHON_PATH} app.py\""
            }
        }
    }
}
