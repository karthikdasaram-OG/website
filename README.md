# Distributed CI/CD Pipeline with Jenkins, Docker and Kubernetes

## 📌 Project Overview

This project demonstrates the implementation of a distributed CI/CD pipeline using Jenkins Master-Agent architecture, Docker, DockerHub, and Kubernetes (K3s).

The pipeline automatically builds, tests, and deploys a static website across three EC2 instances.

---

## 🏗 Architecture

```
GitHub Repository
        ↓
EC2-1 (Jenkins Master + Job1-Build)
        ↓
EC2-2 (Test Agent + Job2-Test)
        ↓
EC2-3 (Prod Agent + Job3-Prod + Kubernetes)
        ↓
DockerHub
        ↓
Kubernetes Deployment (2 Replicas)
        ↓
NodePort Service (30008)
```

---

## 🚀 Tech Stack

* Jenkins
* Docker
* DockerHub
* Kubernetes (K3s)
* Git & GitHub
* AWS EC2
* Ubuntu Linux

---

## 🖥 Infrastructure Setup

### EC2-1 : Jenkins Master

Components:

* Jenkins
* Git
* Docker

Responsibilities:

* Executes Job1-Build
* Triggers Job2-Test

---

### EC2-2 : Test Agent

Components:

* Docker
* Java
* Git

Responsibilities:

* Pulls Docker image from DockerHub
* Runs container for testing
* Triggers Job3-Prod

---

### EC2-3 : Production Agent

Components:

* Docker
* K3s Kubernetes
* kubectl

Responsibilities:

* Pulls image from DockerHub
* Creates Kubernetes namespace
* Deploys application to Kubernetes

---

## ⚙ Pipeline Stages

### Job1-Build

* Checkout source code from GitHub
* Build Docker image
* Push image to DockerHub
* Trigger Job2-Test

### Job2-Test

* Pull Docker image from DockerHub
* Run test container
* Trigger Job3-Prod

### Job3-Prod

* Pull Docker image from DockerHub
* Create namespace
* Deploy application to Kubernetes
* Create NodePort service

---

## 📂 Repository Structure

```
website/
│
├── Dockerfile
├── namespace.yaml
├── deployment.yaml
├── service.yaml
├── Jenkinsfile-build
├── Jenkinsfile-test
├── Jenkinsfile-prod
├── README.md
└── Website source files
```

---

## ☸ Kubernetes Configuration

### Deployment

* Namespace: devops
* Replicas: 2

### Service

* Type: NodePort
* Port: 80
* NodePort: 30008

---

## 🔄 CI/CD Workflow

```
GitHub
   ↓
Job1-Build
   ↓
Job2-Test
   ↓
Job3-Prod
   ↓
DockerHub
   ↓
Kubernetes Deployment
   ↓
NodePort Service (30008)
```

---

## 📸 Project Outputs

* Jenkins Master-Agent Architecture
* Successful Build Pipeline
* Docker Image Push to DockerHub
* Test Container Execution
* Kubernetes Deployment with 2 Replicas
* NodePort Service Exposure
* Website Accessible on Port 30008

---

## 🎯 Key Learnings

* Distributed Jenkins Architecture
* Pipeline as Code
* Docker Image Management
* DockerHub Integration
* Kubernetes Deployments and Services
* Namespace Management
* Multi-node CI/CD Implementation
* Infrastructure as Code Principles

---

## Author

**Dasaram Karthik Reddy**

LinkedIn: [www.linkedin.com/in/karthik-dasaram-7bb57a293](http://www.linkedin.com/in/karthik-dasaram-7bb57a293)
