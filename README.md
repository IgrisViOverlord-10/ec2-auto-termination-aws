# ☁️ EC2 Auto-Termination Based on Low CPU Usage

## 📌 Project Overview

This project demonstrates automated lifecycle management of an Amazon EC2 instance using CloudWatch alarms and SNS notifications.
When CPU utilization remains below a defined threshold for a specific duration, the instance is automatically terminated and an email alert is sent.
This setup simulates production-style monitoring, alerting, and cost-optimization automation.

---

## 🏗 Architecture Flow

EC2 Instance  
→ CloudWatch monitors CPUUtilization  
→ If CPU > 5% = OK state  
→ If CPU ≤ 5% (for evaluation period) = ALARM state  
→ SNS Notification + EC2 Termination Action  

**Threshold Value:** 5%  
**Evaluation Period:** 10 minutes (2 datapoints × 5 minutes)

---

## ⚙️ Services Used

- Amazon EC2  
- Amazon CloudWatch  
- Amazon SNS  

---

## 🛠 Implementation Steps

### 1️⃣ Launch EC2 Instance

- Ubuntu 22.04  
- Instance type: t3.micro  
- Deployed in public subnet  
- Security Group:  
  - SSH (22)  
  - HTTP (80 optional)  

---

### 2️⃣ Create SNS Topic

- Type: Standard  
- Created email subscription  
- Confirmed subscription via email  

---

### 3️⃣ Configure CloudWatch Alarm

- Metric: EC2 → CPUUtilization  
- Statistic: Average  
- Period: 5 minutes  
- Threshold: ≤ 5%  
- Evaluation Periods: 2  

---

### 4️⃣ Configure Alarm Actions

When alarm state = **ALARM**:

- Send notification via SNS  
- Automatically terminate EC2 instance  

---

## 🔐 Security Considerations

- Only required ports opened (SSH 22, HTTP 80)  
- Used temporary/test instance for automation testing  
- Confirmed SNS subscription to ensure alert delivery  
- No unnecessary services exposed  

---

## 🎯 Key Outcomes

- Implemented event-driven infrastructure automation  
- Configured CloudWatch alarms for monitoring  
- Integrated SNS for real-time alerting  
- Demonstrated cost-optimization strategy  
- Practiced EC2 lifecycle management  

---

## 🚀 What This Project Demonstrates

- Monitoring & alerting workflow  
- Infrastructure automation  
- Cost-aware cloud architecture  
- Production-style alarm configuration  
- Hands-on AWS operational experience  
