pipeline {
    agent any

    options {
        disableConcurrentBuilds()
        timeout(time: 10, unit: 'MINUTES')
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
                bat 'python --version'
                bat 'python -m pip install --upgrade pip'
                bat 'python -m pip install --upgrade setuptools wheel'
                bat 'python -m pip install -r requirements.txt'
            }
        }

        stage('Run Flask App') {
            steps {
                echo 'Starting Flask App'
                bat 'taskkill /F /IM python.exe /T || exit 0'
                bat 'start cmd /c "python app.py"'
            }
        }
    }
}
