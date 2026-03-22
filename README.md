# ☁️ EC2 Auto-Termination Based on Low CPU Usage

---

## 📌 Project Overview
Automated lifecycle management of Amazon EC2 instances by monitoring CPU utilization and terminating idle instances. 0This setup reduces manual overhead, prevents cost leakage, and demonstrates event-driven infrastructure automation.

---

## 💻 Tech Stack
- **AWS Services:** EC2 (Ubuntu 22.04), CloudWatch, SNS

---

## ❓ Why This Approach?
- Ensures cost optimization by automatically terminating underutilized instances.  
- Event-driven design reduces manual monitoring and human error.  
- Lightweight and practical setup suitable for real-world operational scenarios.

---

## 🏗 Architecture
**Workflow:**  
EC2 Instance → CloudWatch monitors `CPUUtilization` → Alarm triggers (CPU ≤ 5% for 10 mins) → SNS Notification → Automatic EC2 Termination  

---

## ⚙️ Implementation Summary
- EC2 instance launched in a public subnet using t3.micro.  
- CloudWatch alarm configured with a 5% CPU threshold and 10-minute evaluation window.  
- SNS topic created with email subscription for real-time alerts.  
- Alarm action configured to automatically terminate idle instances.

---

## 🛠 Implementation Steps
1. **Launch EC2 Instance**
   - Ubuntu 22.04, t3.micro, public subnet  
   - Security group: SSH (22), HTTP (80 optional)  

2. **Create SNS Topic**
   - Standard topic with email subscription  
   - Confirm subscription via email  

3. **Configure CloudWatch Alarm**
   - Metric: EC2 → `CPUUtilization`  
   - Statistic: Average  
   - Period: 5 minutes  
   - Evaluation: 2 datapoints  
   - Threshold: ≤ 5%  

4. **Configure Alarm Actions**
   - Send notification via SNS  
   - Trigger automatic EC2 termination  

---

## 🔐 Security / Limitations / Considerations
- Only required ports opened (SSH 22, HTTP 80).  
- Instances used for this setup were **tagged specifically for testing/automation**, preventing accidental termination of critical resources.  
- SNS subscription explicitly confirmed to ensure alert delivery.  
- Limitation: Designed for a single instance; not extended to Auto Scaling or multi-instance environments.  

---

## 🚀 Key Outcomes & Learnings
- Implemented event-driven EC2 lifecycle automation using CloudWatch and SNS  
- Achieved automated cost optimization by terminating idle resources  
- Gained hands-on experience in monitoring, alerting, and infrastructure control  
- Understood how operational metrics can directly trigger infrastructure actions  
- Strengthened practical knowledge of AWS services and real-world cloud workflows  

---

## 📂 Repository Files
- `README.md` – Project documentation  
- `Snapshots - 5` – Contains project snapshots   

---

## 📸 Snapshots / Screenshots
- EC2 instance running before termination  
- CloudWatch alarm state transitions  
- SNS topic with confirmed subscription  
- Email notification received  
- EC2 instance terminated automatically  
