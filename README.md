# 🚀 CI/CD Pipeline using Jenkins & AWS EC2

## 📌 Project Overview

This project demonstrates a **complete CI/CD pipeline** using **Jenkins and AWS EC2**, where code changes pushed to GitHub are automatically deployed to a live web server.

👉 The goal is to eliminate manual deployment and ensure faster, reliable releases.

---

## 🧱 Architecture

```
GitHub (Code Repository)
        ↓
Jenkins (CI/CD Pipeline)
        ↓
AWS EC2 (Apache Web Server)
```

<img width="751" height="71" alt="AWs Jenkins drawio" src="https://github.com/user-attachments/assets/16e008ba-fa3d-4727-91f6-c24174500a8f" />


---

## ⚙️ Tech Stack

* ☁️ AWS EC2 (Web Server)
* 🔧 Jenkins (CI/CD Automation)
* 🐧 Linux (Amazon Linux 2)
* 🌐 Apache (HTTP Server)
* 💻 GitHub (Source Code)

---

## 🚀 Features

* ✅ Automated deployment on code changes
* ✅ Continuous Integration using Jenkins
* ✅ Continuous Deployment to EC2
* ✅ Zero manual intervention
* ✅ Fast and reliable delivery

---

## 🛠️ Setup & Implementation

### 1️⃣ Launch EC2 Instance

* Amazon Linux 2
* Instance Type: t2.micro (Free Tier)
* Open Ports:

  * 22 (SSH)
  * 80 (HTTP)
  * 8080 (Jenkins)

---

### 2️⃣ Install Apache Web Server

```bash
sudo yum update -y
sudo yum install httpd -y
sudo systemctl start httpd
sudo systemctl enable httpd
```

---

### 3️⃣ Install Jenkins

```bash
sudo yum install java-17-amazon-corretto -y

sudo wget -O /etc/yum.repos.d/jenkins.repo \
https://pkg.jenkins.io/redhat-stable/jenkins.repo

sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key

sudo yum install jenkins -y
sudo systemctl start jenkins
sudo systemctl enable jenkins
```

Access Jenkins:

```
http://<EC2-PUBLIC-IP>:8080
```

Unlock Jenkins:

```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

---

### 4️⃣ Configure Jenkins Job

* Create **Freestyle Project**
* Connect GitHub repository
* Enable **Poll SCM**

```
* * * * *
```

---

### 5️⃣ Deployment Script

```bash
sudo cp -r * /var/www/html/
```

Fix permissions:

```bash
sudo chmod -R 777 /var/www/html
```

---

## 🔁 CI/CD Workflow

1. Developer pushes code to GitHub
2. Jenkins detects changes
3. Jenkins pulls latest code
4. Deployment script runs
5. Website updates automatically

---

## 🧪 Testing

* Update `index.html` in GitHub
* Commit changes
* Jenkins auto-build triggers
* Refresh EC2 public IP → changes visible

---

## 📜 Jenkins Pipeline (Jenkinsfile)

```groovy
pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git 'YOUR_REPO_URL'
            }
        }

        stage('Deploy') {
            steps {
                sh 'sudo cp -r * /var/www/html/'
            }
        }
    }
}
```

---

## 🎯 Key Learnings

* CI/CD pipeline fundamentals
* Jenkins automation
* AWS EC2 deployment
* Linux server management
* Real-time deployment handling

---

## 📊 Outcome

* 🚀 Reduced manual deployment effort
* ⚡ Faster delivery cycles
* 🔁 Automated end-to-end deployment
* 💼 Built production-like DevOps workflow

---

## 🌐 Connect With Me

* LinkedIn: https://linkedin.com/in/farish98

---
