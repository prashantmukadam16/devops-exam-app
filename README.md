# 🚀 DevSecOps 3-Tier Application Architecture on AWS

![DevSecOps](https://img.shields.io/badge/DevSecOps-CI%2FCD-blue)
![Jenkins](https://img.shields.io/badge/Jenkins-Automation-red)
![Docker](https://img.shields.io/badge/Docker-Containerization-blue)
![SonarQube](https://img.shields.io/badge/SonarQube-Code%20Quality-green)
![Trivy](https://img.shields.io/badge/Trivy-Security-orange)
![AWS](https://img.shields.io/badge/AWS-Cloud-yellow)

## 📌 Project Overview

This repository demonstrates a complete **Production DevSecOps CI/CD Pipeline** implementation for a **3-Tier Application Architecture** deployed on AWS.
The objective of this project is to automate the entire software delivery lifecycle while integrating security controls at every stage of the pipeline.
The implementation follows the Shift-Left Security Model, ensuring vulnerabilities and code quality issues are detected before deployment.

# 🎯 Project Objectives

* ✅ Automate application delivery using Jenkins
* ✅ Implement a secure CI/CD pipeline
* ✅ Perform static code analysis using SonarQube
* ✅ Scan container images for vulnerabilities using Trivy
* ✅ Push container images to Docker Hub
* ✅ Deploy applications automatically on AWS EC2
* ✅ Implement DevSecOps security best practices
* ✅ Enable continuous monitoring and validation
* ✅ Enforce quality gates before deployment
* ✅ Integrate security into every stage of the CI/CD lifecycle
* ✅ Improve deployment reliability and consistency
* ✅ Reduce manual intervention through automation
* ✅ Adopt Shift-Left Security principles
* ✅ Build a scalable and production deployment workflow


The complete workflow automates the software delivery lifecycle from source code commit to production deployment.

---

# 🏗️ Production Architecture

## High-Level Architecture Diagram

```text
┌─────────────────────┐
│     Developers      │
│  Source Code Push   │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│      GitHub         │
│ Source Repository   │
└──────────┬──────────┘
           │ Webhook
           ▼
┌─────────────────────────────────────────┐
│             Jenkins Server              │
│              CI/CD Engine               │
│                                         │
│  • Checkout                             │
│  • Build                                │
│  • Test                                 │
│  • Security Validation                  │
└───────┬──────────────┬──────────────────┘
        │              │
        ▼              ▼
┌───────────────┐ ┌───────────────┐
│ SonarQube     │ │ Trivy Scanner │
│ SAST Analysis │ │ CVE Analysis  │
└───────┬───────┘ └───────┬───────┘
        │                 │
        └────────┬────────┘
                 ▼
┌────────────────────────────┐
│      Docker Build          │
│ Application Container      │
└─────────────┬──────────────┘
              ▼
┌────────────────────────────┐
│      Docker Hub            │
│ Secure Image Registry      │
└─────────────┬──────────────┘
              ▼
┌────────────────────────────┐
│ AWS Production Server      │
│ Docker Runtime             │
└─────────────┬──────────────┘
              ▼
┌──────────────────────────────────────┐
│      3-Tier Application              │
│                                      │
│ Frontend (React) : Port 3000         │
│ Backend  (NodeJS): Port 5000         │
│ Database (MySQL) : Port 3306         │
└──────────────────────────────────────┘
```

---

# 🎯 Solution Architecture

## Architecture Components

| Component  | Purpose                          |
| ---------- | -------------------------------- |
| GitHub     | Source Code Management           |
| Jenkins    | CI/CD Orchestration              |
| SonarQube  | Code Quality & Security Analysis |
| Trivy      | Vulnerability Scanning           |
| Docker     | Containerization                 |
| Docker Hub | Image Registry                   |
| AWS EC2    | Application Hosting              |
| MySQL      | Data Persistence                 |

---

# 🔄 End-to-End DevSecOps Workflow

```text
Developer Commit
        │
        ▼
GitHub Repository
        │
        ▼
Jenkins Trigger
        │
        ▼
Source Checkout
        │
        ▼
Application Build
        │
        ▼
Code Testing
        │
        ▼
SonarQube Analysis
        │
        ▼
Quality Gate Validation
        │
        ▼
Docker Image Build
        │
        ▼
Trivy Vulnerability Scan
        │
        ▼
Docker Hub Push
        │
        ▼
AWS EC2 Deployment
        │
        ▼
Application Verification
```

---

# 📂 Repository Structure

```text
3-Tier-Application-Architecture-DevSecOps
│
├── Jenkinsfile
│
├── install-scripts
│   ├── 1st-jenkins.sh
│   ├── 2nd-docker.sh
│   ├── 3rd-Adduser+python.sh
│   └── 4th-trivy.sh
│
├── frontend
│   ├── admin.html
│   ├── exam.html
│   ├── index.html
│   └── result.html
│
├── backend
│   ├── Dockerfile
│   ├── app.py
│   └── questions.py
│
├── db
│   └── init.sql
│
├── docker-compose.yml
│
├── screenshots
│   ├── jenkins
│   ├── sonarqube
│   ├── trivy
│   └── application
│
└── README.md
```

---

# 🔐 Security Controls

## SonarQube Security Analysis

Features:

* Static Code Analysis
* Security Hotspots Detection
* Code Smell Detection
* Vulnerability Detection
* Quality Gate Validation

---

## Trivy Container Security

Features:

* OS Vulnerability Scanning
* Library Vulnerability Detection
* Secret Scanning
* Misconfiguration Detection

---

## Jenkins Security

Features:

* Credential Management
* Secret Masking
* Secure Pipeline Execution
* Role-Based Access Control

---

# ⚙️ Jenkins Pipeline Flow

## Pipeline Stages

```text
1. Git Checkout

2. Install Dependencies

3. Build Application

4. SonarQube Analysis

5. Quality Gate Validation

6. Docker Build

7. Trivy Scan

8. Docker Push

9. Deployment

10. Health Check
```

---

# 🚀 Complete Deployment Guide

# Step 1: Launch AWS EC2 Instance

### Configuration

```text
AMI           : Ubuntu 26.04
Instance Type : c7i-flex.large
Storage       : 50 GB
Security Group: Custom
Key Pair	  : Required
Instance Name : DevSecOps

```

---

# Step 2: Configure Security Groups

| Port | Description |
| ---- | ----------- |
| 22   | SSH         |
| 80   | HTTP        |
| 3000 | Frontend    |
| 5000 | Backend     |
| 8080 | Jenkins     |
| 9000 | SonarQube   |
| 3306 | MySQL       |

---

# Step 3: Connect to Server

```bash
Connect SSH to the EC2 Instance using MobaXterm tool 
```

---

# Step 4: Clone Repository

```bash
git clone https://github.com/<your repo>/3-Tier-Application-Architecture-DevSecOps.git

cd 3-Tier-Application-Architecture-DevSecOps
```

---

# Step 5: Install Jenkins

```bash
chmod +x *.sh

sudo apt update
sudo apt install fontconfig openjdk-21-jre
java -version

sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2026.key
echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt update
sudo apt install jenkins
```

Verify:

```bash
systemctl status jenkins
```

---

# Step 6: Install Docker

```bash

./2nd-Docker.sh
```

Verify:

```bash
docker --version
```

---

# Step 7: Install Python and Adduser

```bash

./3rd-Adduser+python.sh
```

---

# Step 7: Install Trivy

```bash

./4th-Trivy.sh
```

Verify:

```bash
trivy --version
```

---

# Step 8: Deploy SonarQube

```bash
docker run -d \
--name sonarqube \
-p 9000:9000 \
sonarqube:lts-community
```

Access:

```text
http://YOUR SONARQUBE SERVER-IP:9000
```

---

# Step 9: Configure Jenkins

Open:

```text
http://YOUR JENKINS SERVER-IP:8080
```

Get Initial Password:

```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

---

# Step 10: Install Required Plugins

```text
Docker
Docker Pipeline
Docker Commons
Pipeline
Pipeline Stage View
SonarQube Scanner
GitHub
Credentials Binding
```

---

# Step 11: Configure SonarQube

```text
Manage Jenkins
→ Configure System
→ SonarQube Servers
```

Add:

```text
Name: SonarQube
URL : http://YOUR SONARQUBE SERVER-IP:9000
```

---

# Step 12: Configure Jenkins Tools

```text
Manage Jenkins
→ Global Tool Configuration
```

Add:

```text
sonar-scanner
docker
```

---

# Step 13: Add Jenkins Credentials

## Docker Hub

```text
ID: docker-hub
```

## Sonar Token

```text
ID: sonar-token
```

---

# Step 14: Configure SonarQube Webhook

```text
http://YOUR JENKINS SERVER-IP:8080/sonarqube-webhook/
```

---

# Step 15: Create Jenkins Pipeline

> Important: This project uses **Pipeline Script** directly inside Jenkins Job Configuration and **NOT Pipeline Script from SCM**.

### Jenkins Job Configuration

```text
New Item
→ Pipeline
→ Definition
→ Pipeline Script
```

Copy the complete Jenkins pipeline script from:

```text
Jenkinsfile
```

Paste directly into Jenkins Pipeline Script section.

Save and Build.

---

# Step 16: Execute Pipeline

Pipeline automatically performs:

```text
Git Checkout
Build
Test
SonarQube Scan
Quality Gate
Docker Build
Trivy Scan
Docker Push
Deployment
Health Check
```

---

# 🌐 Application Access

| Service     | URL                                            |
| ----------- | ---------------------------------------------- |
| Frontend    | [http://SERVER-IP:3000](http://SERVER-IP:3000) |
| Backend API | [http://SERVER-IP:5000](http://SERVER-IP:5000) |
| Jenkins     | [http://YOUR JENKINS SERVER-IP:8080](http://SERVER-IP:8080) |
| SonarQube   | [http://YOUR SONARQUBE SERVER-IP:9000](http://SERVER-IP:9000) |

---

# 📊 Production Readiness Features

✅ CI/CD Automation

✅ Infrastructure Automation

✅ Security Shift Left

✅ Container Security

✅ Automated Quality Gates

✅ Continuous Deployment

✅ Dockerized Application

✅ Secure Credential Management

✅ Vulnerability Management

✅ Production Deployment Workflow

---

# 🛠️ Technology Stack

| Category               | Technology    |
| ---------------------- | ------------- |
| SCM                    | GitHub        |
| CI/CD                  | Jenkins       |
| Security               | SonarQube     |
| Vulnerability Scanning | Trivy         |
| Containerization       | Docker        |
| Registry               | Docker Hub    |
| Cloud                  | AWS EC2       |
| Database               | MySQL         |
| OS                     | Ubuntu Linux  |
| Scripting              | Shell, Groovy |

---

# 📸 Recommended Screenshots Section

Add screenshots under `/screenshots` folder:

```text
screenshots/
├── architecture.png
├── jenkins-dashboard.png
├── sonar-dashboard.png
├── trivy-scan.png
├── dockerhub-image.png
├── pipeline-success.png
└── application-running.png
```

---

# 👨‍💻 Author

**Prashant Mukadam**

DevOps | Cloud | DevSecOps Engineer

---

## Microsoft Visio HLD Diagram



This gives the repository a production-grade appearance suitable for GitHub portfolios, interviews, LinkedIn showcases, and DevSecOps demonstrations.
