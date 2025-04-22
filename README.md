# 📊 EC2 CloudWatch Monitoring Stack

This project sets up a full-stack observability solution for an EC2-hosted website using Amazon CloudWatch. It includes a custom dashboard, metric alarms, and log forwarding from the EC2 instance using the CloudWatch Agent.

---

## 🚀 Features

- 📈 **Real-time CloudWatch Dashboard** for CPU, memory, disk, and network
- 🔔 **Alarms** on key metrics (e.g., CPU > 80%, disk usage)
- 📦 **CloudWatch Agent** installer to stream EC2 logs and metrics
- 🤖 Optional **GitHub Actions** deployment for Infrastructure as Code
- 🧩 Modular and customizable setup for production use

---

## 🛠️ Stack

- **AWS EC2** (Amazon Linux 2)
- **Amazon CloudWatch**
- **CloudFormation** for infrastructure setup
- **Shell scripts** for agent installation
- **GitHub Actions** (optional for CI/CD)

---

## 📁 Repo Structure
