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

