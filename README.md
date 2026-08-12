# Banking App DevOps Project (FundMe Microservice)

## 🏦 Project Overview
This project implements a full **DevOps CI/CD pipeline** for a banking microservice, developed as a certification project for the **Banking and Finance domain**.

The project addresses the real-world business challenges of **FundMe**, a global banking and financial services provider based in Germany. As the company grew, its monolithic application architecture caused difficulties in:
- Managing infrastructure and deployments.
- Scaling individual modules when traffic increased.
- Delivering updates to production quickly and reliably.

This solution transitions FundMe to a **microservices-based architecture** with fully automated CI/CD, enabling faster, high-quality, and scalable deployments on AWS.

## 🎯 Project Objectives
- Automate the build, test, and deployment of a Java Spring Boot microservice.
- Containerize the application using **Docker** and orchestrate with **Kubernetes**.
- Provision infrastructure and configure servers using **Terraform** and **Ansible**.
- Implement automated monitoring and visualization using **Prometheus** and **Grafana**.

## 🛠️ Tech Stack
- **CI/CD:** Jenkins (Master-Slave Architecture)
- **Containerization:** Docker, DockerHub
- **Orchestration:** Kubernetes (AWS EKS)
- **Infrastructure as Code:** Terraform, Ansible
- **Cloud:** AWS (EC2, EKS)
- **Monitoring:** Prometheus, Grafana
- **Application:** Java Spring Boot, Maven

- ## 🔄 CI/CD Pipeline Workflow

The pipeline is triggered automatically on every push to the `main` branch and consists of 6 stages:

| Stage | Description |
| :--- | :--- |
| **1. SCM Checkout** | Jenkins pulls the latest Java source code from GitHub. |
| **2. Maven Build** | Compiles the Java code and runs JUnit/TestNG tests. |
| **3. Docker Build** | Builds a container image from the `Dockerfile`. |
| **4. Login to DockerHub** | Authenticates using Jenkins stored credentials. |
| **5. Push to DockerHub** | Pushes the image to `pramodr0232/banking-app:latest`. |
| **6. Deploy to Kubernetes** | Applies the YAML manifest to the cluster using `kubectl`. |

## 📂 Project Structure
banking-app-cicd/
├── application/ # Spring Boot source code, pom.xml, Dockerfile
├── kubernetes/ # Kubernetes Deployment & NodePort Service YAML
├── jenkins/ # Jenkinsfile (6-stage declarative pipeline)
└── README.md # This documentation

## 🚀 Live Application Access

The application is deployed to a Kubernetes cluster and exposed via a **NodePort service**. It can be accessed at: http://<MASTER_ELASTIC_IP>:31022

> **Note:** Replace `<MASTER_ELASTIC_IP>` with the actual Elastic IP of your Kubernetes Master instance.

## 📊 Monitoring & Observability

A dedicated monitoring server is configured with **Prometheus** and **Grafana** to provide real-time visibility into the application's performance.

**Key Metrics Visualized:**
- JVM Memory Usage (Heap & Non-Heap)
- Application Uptime
- Active Threads
- Garbage Collection Pause Time

The Grafana dashboard is accessible at: http://<MONITORING_PUBLIC_IP>:3000

- **Username:** `admin`
- **Password:** `1234`

## ✅ Project Status

This project is fully functional and has been successfully deployed and tested on AWS. The CI/CD pipeline is stable, the monitoring stack is live, and the application is running in a production-like Kubernetes environment.
