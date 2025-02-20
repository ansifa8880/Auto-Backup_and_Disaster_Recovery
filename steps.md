### 🌳 *Auto Backup and Disaster Recovery in AWS*  

*1. Amazon EC2 (Compute Layer)*  
├── *1.1 Launch Primary EC2 Instance*  
│   ├── Choose AMI, instance type, and configure networking  
│   └── Install and configure applications  
├── *1.2 Launch Secondary EC2 Instance (Failover)*  
│   ├── Choose same AMI and instance type for failover  
│   └── Deploy in a different availability zone for high availability  
└── *1.3 Elastic IP (Optional)*  
    └── Assign Elastic IP for both instances (if needed)  

---

*2. AWS Backup Service*  
├── *2.1 Automated Backup*  
│   ├── Create a Backup Vault to store backups  
│   ├── Define a Backup Plan (daily/weekly)  
│   │   └── Select EC2 instances as backup resources  
│   └── Assign IAM Role with backup permissions  
└── *2.2 Manual Backup (Optional)*  
    └── Use AWS Backup console to create on-demand backups  

---

*3. Route 53 (DNS and Failover Routing)*  
├── *3.1 Configure DNS Record for Primary Server*  
│   ├── Create A record with Elastic IP of Primary EC2  
│   └── Set routing policy as *Failover (Primary)*  
├── *3.2 Configure DNS Record for Secondary Server*  
│   ├── Create A record with Elastic IP of Secondary EC2  
│   └── Set routing policy as *Failover (Secondary)*  
└── *3.3 Health Check Setup*  
    ├── Monitor HTTP/HTTPS endpoint of Primary EC2  
    ├── Define failure threshold and interval  
    └── Associate health check with Primary DNS record  

---

*4. Disaster Recovery (Failover Process)*  
├── *4.1 Primary Server Failure Detected* (Health check fails)  
└── *4.2 Route 53 Automatically Switches to Secondary Server*  

---

*5. IAM Permissions (Security Layer)*  
└── Grant necessary IAM permissions for EC2, Route 53, and AWS Backup services