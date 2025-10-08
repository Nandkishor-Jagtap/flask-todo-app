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
                // Upgrade pip safely
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
                // Kill previous Python process if running (ignore errors)
                bat 'taskkill /F /IM python.exe /T || exit 0'

                // Start Flask app in a new background window
                bat """
                    start "" cmd /c "${env.PYTHON_PATH} app.py"
                    echo Flask app started in background
                """
            }
        }
    }

    post {
        failure {
            echo 'Build failed! Check logs for details.'
        }
        success {
            echo 'Build completed successfully!'
        }
    }
}
