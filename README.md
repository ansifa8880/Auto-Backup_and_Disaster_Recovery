 **🌟 AWS Disaster Recovery & Automated Backups 🚀**  

## **📌 Project Overview**  
This project **automates backups** for an EC2 instance and sets up a **disaster recovery (DR) plan** using AWS services. It ensures **high availability** with failover routing, a load balancer, and AWS Elastic Disaster Recovery (AWS DRS).  

💾 **Automated Backups** | 🌍 **Disaster Recovery** | 🔄 **Failover Mechanism**  

## **🛠️ Key Components**  
- **💻 Amazon EC2** – Primary and DR instances in different AWS regions.  
- **🔄 AWS Backup** – Automates periodic backups of the primary instance.  
- **⚡ AWS Elastic Disaster Recovery (DRS)** – Enables fast recovery in case of failure.  
- **🖥️ Application Load Balancer (ALB)** – Manages traffic distribution.  
- **🌐 Route 53** – Ensures **seamless failover** with health checks.  

## **⚙️ Setup Steps**  
✅ **Step 1:** **Launch EC2 Instances** – Deploy primary and DR instances in different AWS regions.  
✅ **Step 2:** **Configure AWS Backup** – Automate scheduled backups of the primary instance.  
✅ **Step 3:** **Enable AWS DRS** – Set up real-time replication for disaster recovery.  
✅ **Step 4:** **Deploy Load Balancer** – Create an ALB for high availability.  
✅ **Step 5:** **Configure Route 53** – Set up failover DNS records with health checks.  
✅ **Step 6:** **Test Failover** – Simulate failure & ensure automatic redirection to DR instance.  

## **🚀 Why This Setup?**  
🔹 **High Availability** – Failover ensures zero downtime!  
🔹 **Automated Protection** – Backups and replication secure your data.  
🔹 **Scalability** – Seamless transition between primary & DR locations.  
🔹 **Cost Optimization** – Efficient use of AWS resources.  

## **🔎 Best Practices**  
🔹 **Use Low TTL Values** – Ensures faster DNS propagation.  
🔹 **Regular Failover Testing** – To validate disaster recovery readiness.  
🔹 **Optimize Backup Retention** – Balance between cost & recovery needs.  

---

⚡ **With this setup, your infrastructure is disaster-ready and resilient!** 💪🌍  

