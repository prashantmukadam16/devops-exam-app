🚀 DevSecOps 3-Tier Application Architecture on AWS












📌 Project Overview

This repository demonstrates a complete Production-Ready DevSecOps CI/CD Pipeline implementation for a 3-Tier Application Architecture deployed on AWS.

The project integrates:

Continuous Integration (CI)
Continuous Delivery (CD)
Static Application Security Testing (SAST)
Container Security Scanning
Automated Docker Image Management
Continuous Deployment
Shift-Left Security Practices

The complete workflow automates the software delivery lifecycle from source code commit to production deployment.

🏗️ Production Architecture
High-Level Architecture Diagram
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

🎯 Solution Architecture

Architecture Components
Component	Purpose
GitHub	Source Code Management
Jenkins	CI/CD Orchestration
SonarQube	Code Quality & Security Analysis
Trivy	Vulnerability Scanning
Docker	Containerization
Docker Hub	Image Registry
AWS EC2	Application Hosting
MySQL	Data Persistence

🔄 End-to-End DevSecOps Workflow

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

📂 Repository Structure

3-Tier-Application-Architecture-DevSecOps
│
├── Jenkinsfile
│
├── install-scripts
│   ├── install-jenkins.sh
│   ├── install-docker.sh
│   ├── install-python.sh
│   └── install-trivy.sh
│
├── frontend
│   ├── src
│   ├── public
│   ├── package.json
│   └── Dockerfile
│
├── backend
│   ├── src
│   ├── package.json
│   └── Dockerfile
│
├── database
│   └── mysql-init.sql
│
├── deployment
│   ├── docker-compose.yml
│   └── deployment.sh
│
├── screenshots
│   ├── jenkins
│   ├── sonarqube
│   ├── trivy
│   └── application
│
└── README.md

🔐 Security Controls
SonarQube Security Analysis

Features:

Static Code Analysis
Security Hotspots Detection
Code Smell Detection
Vulnerability Detection
Quality Gate Validation
Trivy Container Security

Features:

OS Vulnerability Scanning
Library Vulnerability Detection
Secret Scanning
Misconfiguration Detection
Jenkins Security

Features:

Credential Management
Secret Masking
Secure Pipeline Execution
Role-Based Access Control
⚙️ Jenkins Pipeline Flow
Pipeline Stages
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
🚀 Complete Deployment Guide
Step 1: Launch AWS EC2 Instance
Configuration
AMI           : Ubuntu 22.04
Instance Type : t2.large
Storage       : 50 GB
Step 2: Configure Security Groups
Port	Description
22	SSH
80	HTTP
3000	Frontend
5000	Backend
8080	Jenkins
9000	SonarQube
3306	MySQL
Step 3: Connect to Server
ssh -i key.pem ubuntu@PUBLIC-IP
Step 4: Clone Repository
git clone https://github.com/prashantmukadam16/3-Tier-Application-Architecture-DevSecOps.git

cd 3-Tier-Application-Architecture-DevSecOps
Step 5: Install Jenkins
chmod +x install-scripts/install-jenkins.sh

./install-scripts/install-jenkins.sh

Verify:

systemctl status jenkins
Step 6: Install Docker
chmod +x install-scripts/install-docker.sh

./install-scripts/install-docker.sh

Verify:

docker --version
Step 7: Install Trivy
chmod +x install-scripts/install-trivy.sh

./install-scripts/install-trivy.sh

Verify:

trivy --version
Step 8: Deploy SonarQube
docker run -d \
--name sonarqube \
-p 9000:9000 \
sonarqube:lts-community

Access:

http://SERVER-IP:9000
Step 9: Configure Jenkins

Open:

http://SERVER-IP:8080

Get Initial Password:

sudo cat /var/lib/jenkins/secrets/initialAdminPassword
Step 10: Install Required Plugins
Docker
Docker Pipeline
Docker Commons
Pipeline
Pipeline Stage View
SonarQube Scanner
GitHub
Credentials Binding
Step 11: Configure SonarQube
Manage Jenkins
→ Configure System
→ SonarQube Servers

Add:

Name: SonarQube
URL : http://SERVER-IP:9000
Step 12: Configure Jenkins Tools
Manage Jenkins
→ Global Tool Configuration

Add:

sonar-scanner
docker
Step 13: Add Jenkins Credentials
Docker Hub
ID: docker-hub
Sonar Token
ID: sonar-token
Step 14: Configure SonarQube Webhook
http://SERVER-IP:8080/sonarqube-webhook/
Step 15: Create Jenkins Pipeline

Important: This project uses Pipeline Script directly inside Jenkins Job Configuration and NOT Pipeline Script from SCM.

Jenkins Job Configuration
New Item
→ Pipeline
→ Definition
→ Pipeline Script

Copy the complete Jenkins pipeline script from:

Jenkinsfile

Paste directly into Jenkins Pipeline Script section.

Save and Build.

Step 16: Execute Pipeline

Pipeline automatically performs:

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
🌐 Application Access
Service	URL
Frontend	http://SERVER-IP:3000
Backend API	http://SERVER-IP:5000
Jenkins	http://SERVER-IP:8080
SonarQube	http://SERVER-IP:9000
📊 Production Readiness Features

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

🛠️ Technology Stack
Category	Technology
SCM	GitHub
CI/CD	Jenkins
Security	SonarQube
Vulnerability Scanning	Trivy
Containerization	Docker
Registry	Docker Hub
Cloud	AWS EC2
Database	MySQL
OS	Ubuntu Linux
Scripting	Shell, Groovy
📸 Recommended Screenshots Section

Add screenshots under /screenshots folder:

screenshots/
├── architecture.png
├── jenkins-dashboard.png
├── sonar-dashboard.png
├── trivy-scan.png
├── dockerhub-image.png
├── pipeline-success.png
└── application-running.png

👨‍💻 Author

Prashant Mukadam

DevOps | Cloud | DevSecOps Engineer
