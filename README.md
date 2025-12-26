# 🚀 End-to-End DevOps CI/CD Project on AWS EKS

This project demonstrates an **end-to-end DevOps CI/CD workflow** using AWS, Terraform, Docker, Jenkins, and Kubernetes (EKS).  
It is designed to showcase **real-world DevOps practices**.

---

## 📌 Project Objective

The main objective of this project is to design, automate, and deploy a containerized application on AWS using industry-standard DevOps tools.

This project focuses on:
- Infrastructure provisioning using **Terraform**
- Containerization using **Docker**
- CI/CD automation using **Jenkins**
- Application deployment using **Kubernetes on AWS EKS**

---

## 🧰 Tech Stack Used

- **Cloud Provider**: AWS  
- **Infrastructure as Code**: Terraform  
- **CI/CD Tool**: Jenkins  
- **Containerization**: Docker  
- **Container Registry**: Amazon ECR  
- **Orchestration**: Kubernetes (EKS)  
- **Terraform Backend**: S3 + DynamoDB  
- **Programming Language**: Python (Flask)  
- **Operating System**: Ubuntu (VM-based Jenkins setup)

---

## 🏗️ High-Level Architecture

1. Terraform provisions AWS infrastructure 
2. Jenkins pulls source code from GitHub
3. Jenkins builds a Docker image for the Python application
4. Docker image is pushed to Amazon ECR
5. Jenkins deploys the application to AWS EKS using Kubernetes manifests
6. Kubernetes exposes the application using a LoadBalancer service

---

## 🪜 Project Implementation Steps

### **Step 1: Terraform Backend Configuration**
- Configured an **S3 bucket** to store Terraform state files
- Used **DynamoDB** for state locking
- Prevents concurrent state modification and ensures safe infrastructure updates

**Why this is important:**
- Enables reliable and consistent infrastructure provisioning
- Simulates real-world team-based Terraform usage

---

### **Step 2: Infrastructure Provisioning using Terraform**
Terraform is used to provision:
- VPC and networking components
- AWS EKS cluster
- Worker nodes

**Benefits of using Terraform:**
- Infrastructure is reproducible and version-controlled
- Easy to modify and scale resources
- Widely used industry standard for DevOps

---

### **Step 3: Dockerizing the Python Application**
- Developed a simple Python Flask application
- Created a `Dockerfile` to containerize the application
- Docker image can be built locally and through Jenkins

**Why Docker?**
- Ensures application consistency across environments
- Simplifies deployment to Kubernetes

---

### **Step 4: Continuous Integration (CI) using Jenkins**
A Jenkins pipeline automates the following tasks:
- Pulls latest code from GitHub
- Builds Docker image for the application
- Authenticates securely to Amazon ECR using Jenkins-managed AWS credentials
- Pushes versioned Docker images to Amazon ECR

**Key CI features:**
- Image versioning using Jenkins build numbers
- No hardcoded AWS credentials in the pipeline

---

### **Step 5: Continuous Deployment (CD) to AWS EKS**
- Jenkins deploys the application to EKS using `kubectl`
- Kubernetes manifests (`deployment.yaml` and `service.yaml`) are applied
- Application is exposed externally using a **Kubernetes LoadBalancer service**
- Rolling update strategy ensures smooth application updates

---

## 🔄 CI/CD Pipeline Flow

1. Developer pushes code to GitHub  
2. Jenkins Pipeline is triggered  
3. Jenkins pulls the latest code from GitHub  
4. Docker image is built for the Python application  
5. Jenkins authenticates securely with Amazon ECR  
6. Docker image is tagged using the Jenkins build number  
7. Docker image is pushed to Amazon ECR  
8. Jenkins updates the Kubernetes deployment with the new image  
9. Kubernetes performs a rolling update on AWS EKS  
10. Application is exposed to users via a Kubernetes LoadBalancer


---
