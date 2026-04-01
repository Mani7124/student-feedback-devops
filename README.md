# 🚀 Student Feedback System with CI/CD Pipeline

## 📌 Project Overview

This project is a **Student Feedback System** web application integrated with a **CI/CD pipeline using Jenkins, Docker, and AWS EC2**.

It allows students to:

* Submit feedback
* View previous feedback
* Store feedback in a database

---

## 🛠️ Tech Stack

* **Frontend:** HTML, CSS
* **Backend:** Python (Flask)
* **Database:** SQLite
* **Version Control:** Git & GitHub
* **CI/CD:** Jenkins
* **Containerization:** Docker
* **Deployment:** AWS EC2
* **Automation (Optional):** Ansible

---

## ⚙️ DevOps Pipeline Architecture

```text
GitHub → Jenkins → Docker → Running Application
```

---

## 🚀 Setup & Execution (Step-by-Step)

### 1️⃣ Launch AWS EC2

* Ubuntu 22.04
* Open ports: 22, 8080, 5000

---

### 2️⃣ Install Required Tools

```bash
sudo apt update
sudo apt install openjdk-17-jdk -y
sudo apt install docker.io -y
sudo apt install ansible -y
```

---

### 3️⃣ Install Jenkins

```bash
wget https://pkg.jenkins.io/debian-stable/binary/jenkins_2.492.1_all.deb
sudo apt install ./jenkins_2.492.1_all.deb -y
sudo systemctl start jenkins
```

Access Jenkins:

```
http://<EC2_PUBLIC_IP>:8080
```

---

### 4️⃣ Configure Jenkins Pipeline

* Create new pipeline job
* Select: **Pipeline script from SCM**
* Add GitHub repository URL
* Branch: `main`
* Script Path: `Jenkinsfile`

---

### 5️⃣ Jenkinsfile (Pipeline)

```groovy
pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t feedback-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop feedback-app || true
                docker rm feedback-app || true
                docker run -d -p 5000:5000 --name feedback-app feedback-app
                '''
            }
        }
    }
}
```

---

### 6️⃣ Run Pipeline

* Click **Build Now** in Jenkins
* Monitor console output

---

## 🌐 Access Application

```
http://<EC2_PUBLIC_IP>:5000
```

---

## 🎯 Features

* Submit feedback
* Store feedback in database
* View feedback entries
* Automated CI/CD pipeline

---

## 💡 Learning Outcomes

* Hands-on with CI/CD pipeline
* Jenkins automation
* Docker containerization
* AWS EC2 deployment
* Real-world DevOps workflow

---

## 👨‍💻 Author

**Manikantha (AI & ML Student)**

---

## ⭐ Acknowledgment

This project is developed as part of a **DevOps Mini Project** to understand real-world CI/CD workflows.
