# ☁️ EC2 Auto-Termination Based on Low CPU Usage

## 📌 Project Overview
Automated lifecycle management of EC2 instances by monitoring CPU utilization and terminating idle instances, reducing manual overhead and preventing cost leakage through event-driven automation.

## ❓ Why This Approach?
- Ensures cost optimization by automatically terminating underutilized instances  
- Event-driven design reduces manual monitoring and human error  
- Lightweight and practical setup suitable for real-world operational scenarios  

## 💻 Tech Stack
AWS EC2 (Ubuntu 22.04), CloudWatch, SNS

## 🏗 Architecture Flow
EC2 Instance → CloudWatch monitors `CPUUtilization` → Alarm (CPU ≤ 5% for 1 min) → SNS Notification → Automatic EC2 Termination

## ⚙️ Implementation Summary
- Launched EC2 instance (t3.micro, Ubuntu 22.04) in public subnet  
- Configured CloudWatch alarm with 5% CPU threshold and 1-minute evaluation  
- Created SNS topic with confirmed email subscription for alerts  
- Alarm action triggers automatic termination of idle instance  

## 🛠 Implementation Steps
1. Launch EC2 instance with required security group (SSH 22, HTTP 80 optional)  
2. Create SNS topic and confirm email subscription  
3. Configure CloudWatch alarm for `CPUUtilization` (Average, 60s period, ≤5%)  
4. Set alarm actions to send SNS notification and terminate instance  
5. Verify automated termination workflow via CloudWatch and email alerts  

## 🔐 Security & Considerations
- Only required ports opened  
- Instances tagged for testing/automation to prevent accidental termination  
- SNS subscriptions confirmed for alert delivery  
- Limitation: single-instance setup; not extended to multi-instance or Auto Scaling  

## 🚀 Key Outcomes
- Implemented event-driven EC2 lifecycle automation  
- Achieved automated cost optimization by terminating idle resources  
- Hands-on experience with monitoring, alerting, and operational metrics triggering actions  
- Strengthened understanding of AWS event-driven workflows  

## 📂 Repository Files
- `README.md` – Project documentation  
- `Snapshots.pdf` – Project snapshots  

## 📸 Snapshots Include
- EC2 instance running before termination  
- CloudWatch alarm state transitions  
- SNS topic and confirmed subscription  
- Email notification received  
- EC2 instance automatically terminated
