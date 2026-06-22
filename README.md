# End-to-End CI/CD Pipeline using Jenkins, Docker, Docker Hub and Kubernetes (K3s)

## Project Overview

This project demonstrates an end-to-end CI/CD pipeline for deploying a containerized website application using Jenkins, Docker, Docker Hub, and Kubernetes (K3s).

The pipeline automates building Docker images, pushing them to Docker Hub, and deploying the application to a Kubernetes cluster.

---

## Architecture

```
GitHub
   ↓
Jenkins
   ↓
Docker Build
   ↓
Docker Hub
   ↓
Kubernetes (K3s)
   ↓
Website Deployment
```

---

## Tools and Technologies

* Git & GitHub
* Jenkins
* Docker
* Docker Hub
* Kubernetes (K3s)
* Ubuntu EC2
* YAML
* Groovy (Jenkins Pipeline)

---

## Project Structure

```
website/
│
├── Dockerfile
├── Jenkinsfile
├── deployment.yaml
├── service.yaml
├── index.html
└── README.md
```

---

## Docker Image

Docker Image:

```
karthik19112001/website-app:latest
```

---

## Kubernetes Resources

### Deployment

* Deployment Name: website-deployment
* Replicas: 2

### Service

* Service Name: website-service
* Type: NodePort
* Port: 80
* NodePort: 30008

---

## CI/CD Pipeline Stages

### Stage 1: Source Code Checkout

Fetch source code from GitHub repository.

### Stage 2: Docker Image Build

Build Docker image using Dockerfile.

### Stage 3: Push Image to Docker Hub

Push the latest image to Docker Hub repository.

### Stage 4: Deploy to Kubernetes

Deploy application to Kubernetes cluster using:

* deployment.yaml
* service.yaml

---

## Kubernetes Commands

View nodes:

```bash
kubectl get nodes
```

View pods:

```bash
kubectl get pods -n devops
```

View services:

```bash
kubectl get svc -n devops
```

View all resources:

```bash
kubectl get all -n devops
```

---

## Jenkins Pipeline Workflow

```
GitHub Repository
        ↓
Jenkins Pipeline
        ↓
Docker Image Build
        ↓
Docker Hub Push
        ↓
Kubernetes Deployment
        ↓
Application Available
```

---

## Features

* Automated CI/CD pipeline
* Containerized application deployment
* Docker image management using Docker Hub
* Kubernetes orchestration with K3s
* Jenkins pipeline automation
* Scalable deployment with multiple replicas

---

## Future Enhancements

* Multi-job Jenkins architecture
* Separate Test and Production environments
* Jenkins agents
* GitHub Webhooks
* SonarQube Integration
* Trivy Security Scanning
* Prometheus Monitoring
* Grafana Dashboards
* ArgoCD GitOps
* Terraform Infrastructure Automation

---


DevOps | AWS | Docker | Jenkins | Kubernetes
