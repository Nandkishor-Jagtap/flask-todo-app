pipeline {
    agent any

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
                bat 'python -m pip install --upgrade pip'
                bat 'pip install -r requirements.txt'
            }
        }

        stage('Run Flask App') {
            steps {
                echo 'Starting Flask App'
                // Kill previous instance if running
                bat 'taskkill /F /IM python.exe /T || exit 0'
                // Start Flask app in background
                bat 'start cmd /c "python app.py"'
            }
        }
    }
}
