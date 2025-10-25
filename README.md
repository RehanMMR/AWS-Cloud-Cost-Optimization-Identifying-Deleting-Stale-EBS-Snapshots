# 🌩️ AWS Cloud Cost Optimization — Identifying & Deleting Stale EBS Snapshots 🚀

💭 **Ever checked how many old EBS snapshots your AWS account is holding onto?**  
Those could be quietly adding to your bill every month without you even noticing 💸  

Cloud cost optimization isn’t just about shutting down idle EC2 instances — it’s also about identifying hidden resources that silently consume storage and increase costs.

Recently, I built a **Lambda function using Python (Boto3)** that automatically detects and deletes stale EBS snapshots, helping optimize cloud storage costs and maintain a cleaner AWS environment.

---

## 💡 What’s an EBS Snapshot?

An **EBS (Elastic Block Store) Snapshot** is essentially a **backup of your EC2 volume**, stored in Amazon S3.

It helps with:
1. 🧩 Data recovery after failure  
2. ⚙️ Creating new volumes with the same data  
3. 📦 Maintaining regular backups  

However, **snapshots continue to incur storage costs** even if the related instance or volume has been deleted.  
Over time, these can pile up and **inflate your AWS bill unnecessarily**.

---

## 🧠 How My Lambda Function Works

1. Fetches all EBS snapshots owned by my account.  
2. Lists all active EC2 instances (running or stopped).  
3. For each snapshot, checks if its associated volume is still attached to an instance.  
4. If the snapshot is not linked to any active resource, it automatically deletes it.  

This ensures only **useful snapshots** are retained, directly reducing **wasted storage costs**.

---

## ⚙️ Tech Stack

- **AWS Lambda** (Python runtime)  
- **Boto3** (AWS SDK for Python)  
- **EC2 & EBS Services**  
- **CloudWatch Events** *(optional — for scheduling automatic cleanup)*  

---

## 🧾 Example Use Case

- Created an EC2 instance (with a volume automatically attached).  
- Generated a snapshot of the volume.  
- Wrote a Python script in Lambda that checks if the volume or instance still exists.  
- If no associated instance/volume is found, the snapshot is deleted.  
- Can be triggered manually or automatically via **CloudWatch Event Rules**.

---

## 🧩 Lambda Execution Result (Reference)

Below is an example execution output showing successful deletion of a stale EBS snapshot:

![Lambda Execution Result](<img width="1046" height="483" alt="Screenshot 2025-10-25 124353" src="https://github.com/user-attachments/assets/54d97846-964c-4932-8a3a-0259004668ac" />
)

> ✅ Deleted EBS snapshot as its associated volume was not found — optimizing AWS storage cost automatically!

---

## 💬 Key Takeaway

Even **small automations** can make a **big impact** in cloud cost management.  

With tools like **AWS Lambda** and **Boto3**, we can build **lightweight, serverless solutions** that:
- Run efficiently  
- Save money  
- Require **no manual intervention**

---

## 🏷️ Tags

`#AWS` `#CloudComputing` `#CostOptimization` `#Lambda` `#Python` `#EBS` `#Boto3` `#CloudAutomation`

---

## 📜 Author

**Rehan Mohammed**  
💼 Cloud Enthusiast | AWS Learner |  
🔗 [LinkedIn](www.linkedin.com/in/mohammed-rehan-madanapalli-892915316)

