# Deploying a Microservices Application on AWS EKS

This project demonstrates deploying a microservices-based application on **Amazon Elastic Kubernetes Service (EKS)** using **Terraform** for infrastructure automation, **Jenkins** for CI/CD, **Helm** for deployment, and **Prometheus & Grafana** for monitoring. The infrastructure also includes an **Ingress Controller** for managing external access.

## **Technologies Used**

- **Infrastructure Provisioning:** Terraform
- **Container Registry:** Amazon Elastic Container Registry (ECR)
- **Orchestration:** Amazon Elastic Kubernetes Service (EKS)
- **CI/CD Pipeline:** Jenkins
- **Deployment Management:** Helm
- **Monitoring & Logging:** Prometheus, Grafana
- **Ingress Controller:** Nginx (deployed via Terraform)

## **Project Workflow**

1. **Create ECR Repositories** using Terraform
2. **Build and Push Docker Images** to ECR using a Shell Script
3. **Provision an EKS Cluster** using Terraform
4. **Set Up a Jenkins Pipeline** to automate the deployment
5. **Deploy Microservices** using Helm Charts
6. **Monitor with Prometheus and Grafana**
7. **Configure Ingress Controller** using Terraform

## **Getting Started**

### **Prerequisites**

- AWS account with IAM permissions
- AWS CLI installed and configured
- Docker installed
- Terraform installed
- Helm installed
- Jenkins server set up

---

## **1️⃣ Create Amazon ECR Repositories**

Use Terraform to create and manage ECR repositories, ensuring a centralized location for storing container images.

---

## **2️⃣ Build & Push Docker Images to ECR**

Build Docker images for microservices, tag them appropriately, and push them to the ECR repository for deployment.

---

## **3️⃣ Provision Amazon EKS Cluster**

Use Terraform to provision an EKS cluster with the required networking and IAM configurations, ensuring a scalable and secure environment.

---

## **4️⃣ Set Up Jenkins CI/CD Pipeline**

Configure Jenkins to automate the build, push, and deployment process using a structured pipeline.

---

## **5️⃣ Deploy Microservices Using Helm**

Use Helm charts to simplify the deployment and management of microservices within the EKS cluster.

---

## **6️⃣ Monitoring with Prometheus and Grafana**

Set up Prometheus for metric collection and Grafana for visualization, ensuring real-time monitoring of the application.

---

## **7️⃣ Configure Ingress Controller**

Deploy an Nginx Ingress Controller using Terraform to manage external access to microservices efficiently.

---

## **✅ Accessing the Application**

Retrieve the Kubernetes Load Balancer or Minikube IP to access the application, ensuring proper exposure of services.

---

## **🚀 Conclusion**

This project provides a complete workflow for deploying a **microservices-based application on AWS EKS**, automating infrastructure with **Terraform**, handling deployments with **Helm & Jenkins**, and monitoring with **Prometheus & Grafana**.

---

Let me know if you'd like additional modifications or enhancements! 😊

