# 📝 Flask To-Do App

A simple and elegant **To-Do List Web Application** built using **Python Flask**, designed to help users manage their daily tasks efficiently.  
This project is integrated with **Jenkins CI/CD** for automated deployment whenever new changes are pushed to GitHub.

---

## 🚀 Features

- ➕ Add new tasks  
- ✅ Mark tasks as completed  
- 🗑️ Delete tasks  
- 📝 Edit existing tasks  
- 💾 Data stored locally using SQLite  
- 🔁 Auto-deployment using Jenkins pipeline  

---

## 🛠️ Tech Stack

| Component     | Technology Used        |
|----------------|-----------------------|
| Language       | Python (3.11+)        |
| Framework      | Flask                 |
| Database       | SQLite                |
| Automation     | Jenkins CI/CD         |
| Version Control| Git & GitHub          |

---

## ⚙️ Project Setup

### 1. Clone the Repository

git clone https://github.com/Nandkishor-Jagtap/flask-todo-app.git
cd flask-todo-app

2. Create Virtual Environment (Optional but Recommended)

python -m venv venv
venv\Scripts\activate       # For Windows
source venv/bin/activate    # For Linux/Mac

3. Install Dependencies

pip install -r requirements.txt

4. Run the Flask App

python app.py
Now open your browser and visit 👉
http://127.0.0.1:5000 or http://localhost:5000

🤖 Jenkins CI/CD Integration
This repository already includes a Jenkinsfile, so Jenkins automatically detects the pipeline configuration.

Each new GitHub commit triggers:

Pulling the latest code

Installing dependencies

Running the Flask application automatically

The pipeline also ensures only one build runs at a time using disableConcurrentBuilds() — so new commits stop the previous pipeline before starting a new one.

🧩 Folder Structure:
## Folder structure
<pre> <pre> flask-todo-app/ ├── app.py ├── requirements.txt ├── templates/ │ ├── index.html │ └── base.html ├── static/ │ ├── style.css │ └── script.js └── Jenkinsfile </pre> </pre>
