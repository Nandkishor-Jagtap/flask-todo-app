pipeline {
    agent any

    environment {
        // Update this to your system-wide Python path
        PYTHON_PATH = 'C:\\Program Files\\Python311\\python.exe'
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
                // Check if Python exists and install packages
                bat """
                if exist "${env.PYTHON_PATH}" (
                    "${env.PYTHON_PATH}" -m pip install --upgrade pip
                    "${env.PYTHON_PATH}" -m pip install --upgrade setuptools wheel
                    "${env.PYTHON_PATH}" -m pip install -r requirements.txt
                ) else (
                    echo Python executable not found at ${env.PYTHON_PATH}
                    exit 1
                )
                """
            }
        }

        stage('Run Flask App') {
            steps {
                echo 'Starting Flask App'
                // Kill any previous Python process
                bat 'taskkill /F /IM python.exe /T || exit 0'
                // Start Flask app in background
                bat "start cmd /c \"${env.PYTHON_PATH} app.py\""
            }
        }
    }
}
