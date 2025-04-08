# Node.js CI/CD Pipeline with Kubernetes on AWS

This project explains how to deploy an end-to-end **Node.js application** using a complete CI/CD pipeline on AWS.

---

## 🚀 Project Flow

The deployment pipeline includes the following stages:

1. **Build a CI/CD Pipeline**  
2. **Fetch Code from GitHub**
3. **Perform SonarQube Code Analysis**
4. **Run OWASP Dependency Check**
5. **Build Docker Image and Run Trivy Image Scan**
6. **Push Docker Image to Docker Hub**

---

## 🛠️ Kubernetes Deployment

- Write Kubernetes **manifest files**
- Install **Helm** for managing deployments
- Set up **ArgoCD** for GitOps-based deployment
- Implement **monitoring** using Prometheus and Grafana

---

> All steps are automated to ensure smooth, secure, and continuous delivery of the application to a Kubernetes cluster managed with KOPS on AWS.

## 🔧 Setup Instructions

Below are the key steps involved in the complete setup of the Node.js CI/CD pipeline on AWS with Kubernetes, Jenkins, ArgoCD, and monitoring.

---

### ✅ Install Dependencies and Plugins for Jenkins
Install all required Jenkins plugins (e.g., Git, Docker, Pipeline, Blue Ocean, etc.).

[jenkins-plugins](docs/jenkins-plugins.md)

---

### 🔐 Pass the Credentials in Jenkins
Create credentials in Jenkins for:
- GitHub access
- DockerHub authentication
- SonarQube token
- Slack Webhook (optional)

[jenkins-credentials-setup.md](docs/jenkins-credentials-setup.md)

---

### 🔁 Build CI/CD Pipeline
Implement Jenkins pipeline covering:
- GitHub clone
- SonarQube analysis
- OWASP check
- Docker build and scan
- DockerHub push
- Slack/Splunk integration (optional)

[Jenkinsfile](docs/Jenkinsfile.md)

---

### ☸️ Install and Setup KOPS Cluster
Create a production-grade Kubernetes cluster on AWS using KOPS.

[kops-setup.md](docs/kops-setup.md)

---

### 🚀 ArgoCD Setup for GitOps-based Deployment
Install ArgoCD and configure it to auto-sync with Helm charts for app deployment.

[argocd-setup.md](docs/argocd-setup.md)

---

### 📊 Setup Monitoring
Configure Prometheus and Grafana for monitoring and alerting.

[monitoring-setup.md](docs/monitoring-setup.md)

---

