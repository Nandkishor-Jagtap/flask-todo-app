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
                bat '''
                python --version
                python -m pip install --upgrade pip
                python -m pip install --upgrade setuptools wheel
                python -m pip install -r requirement.txt
                '''
            }
        }

        stage('Run Flask App') {
            steps {
                echo 'Starting Flask application...'
                bat '''
                set FLASK_APP=app.py
                set FLASK_ENV=development
                python app.py
                '''
            }
        }
    }
}
