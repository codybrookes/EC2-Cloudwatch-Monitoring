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

## 📁 Repo Structure

```
ec2-cloudwatch-monitoring/
├── cloudwatch/
│   ├── ec2-monitoring-dashboard.json     # Custom dashboard template
│   └── alarms.yml                        # CloudFormation template for alarms
├── scripts/
│   └── install-cloudwatch-agent.sh       # CloudWatch Agent setup script

├── README.md                             # You're here 😎
```

---

## ⚙️ Setup Guide

### 1️⃣ Prerequisites

- An EC2 instance running Amazon Linux 2 or Ubuntu
- AWS CLI installed and configured
- Permissions: `CloudWatchFullAccess`, `CloudFormationFullAccess`

### 2️⃣ Install CloudWatch Agent on EC2

SSH into your instance, then run:

```bash
bash scripts/install-cloudwatch-agent.sh
```

This installs and starts the CloudWatch Agent, configured to collect:
- CPU usage
- Memory utilization
- Disk space used

### 3️⃣ Deploy Metric Alarms

Run from your terminal (update with your real EC2 instance ID):

```bash
aws cloudformation deploy \
  --template-file cloudwatch/alarms.yml \
  --stack-name ec2-monitoring-stack \
  --parameter-overrides InstanceId=i-0abc123def456gh78 \
  --capabilities CAPABILITY_NAMED_IAM
```

This will create:
- 🚨 Alarm for high CPU (>80%)
- ❌ Alarm for system status check failures

### 4️⃣ Import CloudWatch Dashboard

1. Go to **CloudWatch > Dashboards** in AWS Console
2. Click **Create dashboard** → choose **JSON editor**
3. Copy & paste contents of `ec2-monitoring-dashboard.json`
4. Replace `i-xxxxxxxxxxxxxxxxx` with your actual instance ID

---


## 📊 Metrics Monitored

| Metric                  | Description                        |
|------------------------|------------------------------------|
| `CPUUtilization`       | Average CPU usage over time        |
| `NetworkIn/Out`        | Data sent and received             |
| `DiskUsedPercent`      | % of disk usage (from CW Agent)    |
| `mem_used_percent`     | % of memory used (from CW Agent)   |
| `StatusCheckFailed`    | Fails health/status checks         |

---

## 📌 Example Use Cases

- Monitor uptime of your EC2-hosted website
- Detect high traffic spikes or degraded performance
- Observe disk/memory pressure over time
- Automate notifications with SNS or Lambda

---

## 👨‍💻 Author

**Cody Brookes**  

