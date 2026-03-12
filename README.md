# Multi-Tier Microservices CI/CD Pipeline on Kubernetes 🚀

## 📌 Project Overview
A complete End-to-End CI/CD pipeline for a multi-tier microservices application (Python/Flask backend + Redis Database). The project automates the build, push, and deployment processes to a Kubernetes cluster using Jenkins (Pipeline as Code).

## 🏗️ Architecture & Tools
* **Backend:** Python (Flask)
* **Database/Cache:** Redis
* **Containerization:** Docker
* **CI/CD Server:** Jenkins (Declarative Pipeline)
* **Orchestration:** Kubernetes (Minikube)
* **Version Control:** Git & GitHub

## ⚙️ CI/CD Workflow
1. Developer pushes code to the GitHub repository.
2. Jenkins triggers the pipeline using a `Jenkinsfile`.
3. **CI Phase:** Jenkins builds the Docker image.
4. **Delivery Phase:** Jenkins securely logs into Docker Hub using encrypted credentials and pushes the image.
5. **CD Phase:** Jenkins updates the Kubernetes deployment and automatically rolls out the new version with zero downtime.

## 🌐 Kubernetes Infrastructure (Infrastructure as Code)
* **Deployments:** Created a high-availability setup with `3 Replicas` of the Python App, and `1 Replica` of Redis.
* **Services:** Configured internal communication using `ClusterIP` for Redis, and exposed the frontend using `NodePort` for external access.
