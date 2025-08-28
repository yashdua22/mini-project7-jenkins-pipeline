# mini-project7-jenkins-pipeline
# 🚀 Jenkins CI/CD Pipeline with Dockerized Services

## 📌 About
This project sets up a **Jenkins CI/CD pipeline** that automates container deployment for multiple services using Docker.  
The pipeline is designed to run on an EC2 instance with proper security and integrates Slack notifications for build status updates.

---

## ⚙️ Pipeline Stages
1. **Nginx** – Pull and run container on port **80**  
2. **Tomcat** – Pull and run container on port **8081**  
3. **RabbitMQ** – Pull and run container on port **5672**  
4. **Memcached** – Pull and run container on port **11211**  
5. **MySQL 8.0** – Pull and run container on port **3306**  
6. **OS Update** – Update the operating system packages  
7. **Hello World** – Pull and run a simple hello-world container  
8. **Slack Notification** – Send status updates to a Slack channel via bot  

---

## 🛠️ Prerequisites
- **EC2 instance** with:
  - Security group rules:
    - `SSH` (port 22) → Your IP
    - `Jenkins UI` (port 8080) → Your IP
- **Jenkins** installed and running
- **Docker** installed and configured
- **Slack App** with bot token

---

## ⚡ Setup Instructions

### 1. Configure Docker permissions for Jenkins
```bash
sudo usermod -aG docker jenkins
sudo systemctl restart jenkins


2. Install Required Jenkins Plugins

Slack Notification

Docker

3. Configure Slack in Jenkins

Navigate: Manage Jenkins → System → Slack

Add:

Workspace name

Slack channel name

Credentials → Kind: Secret Text, paste your Slack App Token

Test the connection to confirm
