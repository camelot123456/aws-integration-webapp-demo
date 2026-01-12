# 🚀 Deploying Spring Boot App on AWS EC2 - Commands & Descriptions

## ✅ 1. Upload JAR to EC2
```bash
scp -i <your-key.pem> demo.jar ec2-user@<public-ip>:/home/ec2-user/
```
--- 
## ⚡️ 2. SSH into EC2 Instance
### 2.1. Linux/Mac:
```bash
ssh -i <your-key.pem> ec2-user@<public-ip>
```
### 2.2. Windows (Using PowerShell or CMD):
1. Open PowerShell
2. Navigate to the folder containing your `.pem` file
3. Run:
```shell
ssh -i .\your-key.pem ec2-user@<public-ip>
```
### 2.3. Windows (Using PuTTY):
1. Convert `.pem` to `.ppk` using PuTTYgen
1. Open PuTTY
1. Set Host Name: `ec2-user@<public-ip>`
1. Go to Connection > SSH > Auth
1. Browse and select `.ppk` file
1. Click Open to connect

---
## 📦 3. Install Java (Amazon Linux 2, Java 21)
```shell
sudo yum update -y
sudo amazon-linux-extras enable corretto21
sudo yum install java-21-amazon-corretto -y
java -version
```
---

## 🚀 4. Run Spring Boot JAR with nohup
```shell
nohup java -jar demo.jar > output.log 2>&1 &
```
**Explanation:**
- **nohup:** Prevents the app from stopping after logout
- **> output.log:** Saves app logs
- **2>&1:** Also saves error logs
- **&:** Runs in background
---

## 🔍 5. View Logs in Real-Time
```shell
tail -f output.log
```