# 🚀 AWS EKS Application Deployment from Scratch  

This repository documents my hands-on deployment of an application on **Amazon EKS** (Elastic Kubernetes Service) from scratch.  
The setup includes **ALB Ingress Controller**, **OIDC integration**, and a **sample Kubernetes application (2048 game app)** to demonstrate production-grade deployment.  

---

## 📌 Project Overview  

✅ Provisioned an **EKS Cluster** on AWS  
✅ Configured **IAM Roles & Policies** (with `iam_policy.json`)  
✅ Integrated **OIDC provider** for secure service account authentication  
✅ Installed **AWS Load Balancer Controller (ALB Ingress)** for routing external traffic  
✅ Deployed a **sample app (2048 game)** with Ingress configured  
✅ Verified application access via **ALB DNS endpoint**  

---

## 📂 Repository Structure  

eks-app-deployment/
├── prerequisites.md # Pre-requirements (IAM user, AWS CLI, kubectl setup)
├── installing-eks.md # Steps to create an EKS cluster
├── configure-oidc-connector.md # Configure OIDC provider for IAM roles
├── alb-controller-add-on.md # Install AWS Load Balancer Controller
├── sample-app.md # Deploying sample app on EKS
├── 2048-app-deploy-ingress.md # Ingress deployment for 2048 app
├── iam_policy.json # IAM Policy JSON for ALB Controller
└── README.md # Project overview (this file)


---

## ⚙️ Setup Instructions

### 1️⃣ Prerequisites
- AWS CLI & IAM user with programmatic access
- `kubectl` installed
- `eksctl` installed
- Configured AWS credentials

### 2️⃣ Create an EKS Cluster
```bash
eksctl create cluster --name eks-demo --region us-east-1 --nodes 2

eksctl utils associate-iam-oidc-provider --region us-east-1 --cluster eks-demo --approve

kubectl apply -f alb-controller-add-on.yaml

kubectl apply -f 2048-app-deploy-ingress.yaml

kubectl get ingress -n game-2048


Copy the ALB DNS and open it in your browser 🎮

🌟 Key Learnings

Difference between EKS-managed vs. self-managed Kubernetes

Setting up IAM roles and policies securely for Kubernetes workloads

Using Ingress + ALB to expose apps externally

Deploying real-world apps on EKS with persistent networking

📖 References

AWS EKS Documentation

AWS Load Balancer Controller

eksctl Official Docs

[Abhishek Veermalla – EKS Deployment Tutorial (YouTube)](👉 https://youtu.be/RRCrY12VY_s?si=V_Eiesuxw-lT56GK 👈)

💡 This project is part of my DevOps journey — focusing on Kubernetes, AWS, and CI/CD integrations.
