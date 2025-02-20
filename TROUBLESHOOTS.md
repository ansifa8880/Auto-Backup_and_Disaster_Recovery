# 🚀 Troubleshooting Guide: AWS Auto Backup and Disaster Recovery Project 🔧

## 1️⃣ EC2 Instances Not Starting 🖥️❌
🔍 *Cause:* Incorrect instance configuration or availability zone issues.  
✅ *Solution:*  
- ✅ Verify the instance type and AMI selection.  
- ✅ Ensure the availability zone has capacity.  
- ✅ Check security group rules for inbound and outbound connections.  

## 2️⃣ Backup Not Triggering Automatically 💾⏳
🔍 *Cause:* Misconfigured AWS Backup plan or missing instance selection.  
✅ *Solution:*  
- ✅ Ensure the correct EC2 instances are selected in the backup plan.  
- ✅ Verify the backup schedule and time zone.  
- ✅ Check the status of the backup vault and ensure it is accessible.  

## 3️⃣ Route 53 Failover Not Working 🌍🔄
🔍 *Cause:* Misconfigured DNS records, incorrect health checks, or high TTL values.  
✅ *Solution:*  
- ✅ Verify that primary and secondary DNS records are correctly set with failover routing.  
- ✅ Ensure health checks monitor the correct endpoint (IP address or domain name).  
- ✅ Lower the TTL value for faster DNS updates.  

## 4️⃣ Health Check Failing Incorrectly 🏥⚠️
🔍 *Cause:* Incorrect protocol or endpoint in Route 53 health checks.  
✅ *Solution:*  
- ✅ Use the correct protocol (HTTP/HTTPS) and port number.  
- ✅ Ensure the server responds with HTTP status code 2xx or 3xx.  
- ✅ Allow inbound traffic for health checks in the security group.  

## 5️⃣ Failover Delay or No Failover ⏳🔁
🔍 *Cause:* High TTL value, delayed health check detection, or DNS caching.  
✅ *Solution:*  
- ✅ Set a lower TTL value (e.g., 60 seconds).  
- ✅ Reduce the health check interval and failure threshold.  
- ✅ Clear DNS cache on local devices during testing.  

## 6️⃣ Connection Issues to EC2 Instances 🔌🚫
🔍 *Cause:* Firewall, security group, or key pair issues.  
✅ *Solution:*  
- ✅ Allow inbound SSH traffic on port 22 in the security group.  
- ✅ Ensure the correct key pair (.pem file) is used for SSH access.  
- ✅ Check if Elastic IP is correctly assigned to the instance.  

## 7️⃣ Backup Storage Issues 🏦❌
🔍 *Cause:* Insufficient storage in the backup vault or S3 bucket.  
✅ *Solution:*  
- ✅ Verify available space in the backup vault or S3 bucket.  
- ✅ Increase storage limits if necessary.  
- ✅ Delete outdated backups to free up space.  

## 8️⃣ Public IP Address Changes During Failover 🌐🔄
🔍 *Cause:* Using a public IP instead of Elastic IP.  
✅ *Solution:*  
- ✅ Assign Elastic IPs to both primary and secondary instances to maintain consistent IP addresses during failover.  

## 9️⃣ DNS Propagation Delay 🕰️🌎
🔍 *Cause:* High TTL or slow DNS propagation.  
✅ *Solution:*  
- ✅ Set TTL to a low value (60 seconds) for faster updates.  
- ✅ Wait for DNS propagation or flush local DNS cache to test changes.  

## 🔟 Unexpected Billing Costs 💰⚠️
🔍 *Cause:* Running multiple instances or frequent backups.  
✅ *Solution:*  
- ✅ Monitor resource usage using AWS Cost Explorer.  
- ✅ Optimize backup frequency and retention periods.  
- ✅ Stop unused EC2 instances to reduce costs.  

---

### 🛠️ Additional Troubleshooting Cases:

**1️⃣ Failover Verification Issue ❌**  
🔍 *Issue:* Checking failover using `nslookup shoppingcarts.life` but not getting public IPs of primary and secondary instances.  
✅ *Solution:*  
- ✅ Use `nslookup www.shoppingcarts.life` (primary failover record name).  
- ✅ Use `nslookup http.shoppingcarts.life` (secondary failover record name).  
- ✅ Expected Output:  
  1. Primary instance IP address 🏠  
  2. Secondary instance IP address 🔄  

**2️⃣ Primary EC2 Stopped But Still Resolving ❓**  
🔍 *Issue:* After stopping primary EC2 (`shop1`), running `nslookup www.shoppingcarts.life` still returns the primary IP.  
✅ *Solution:*  
- ✅ Used command: `ipconfig /flushdns` to flush DNS resolver cache.  
- ✅ Ensure the health check status is `Unhealthy`.  
- ✅ Leave overnight to allow NS records to update properly.  
- ✅ Next day, running `nslookup` provided the correct failover output.  

🛠️💡 **This guide ensures smooth AWS Disaster Recovery and Backup operations. Regularly test failover scenarios to maintain reliability! 🚀**

