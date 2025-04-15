# DevOps – Day 3: IAM, EC2 Setup, CI/CD Pipeline & Docker Installation

## 🔐 Setting Up AWS IAM Roles

### IAM User Info:
- **Username**:  
- **Initial Password**:  

---

## 🚀 Launching an EC2 Instance on AWS

1. Sign in to your AWS Console.  
2. Search for **EC2** in the services and open the **Dashboard**.  
3. Click **Launch Instance** to begin setup.  
4. Instance Configuration:
   - AMI: Select **Amazon Linux**
   - Type: Choose `t2.micro`
   - Create a new key pair or use an existing one
   - In network settings, make sure **SSH (port 22)** is enabled  
5. Hit **Launch** to spin up the instance.  

---

## 🔁 Implementing a CI/CD Workflow

### Overview of CI/CD Flow:
```bash
START -> INSTANCE (AWS LINUX) -> DEVELOPMENT -> CI POLICY -> EC2 SERVER -> Application Deployment -> END
```
### Pipeline Breakdown:

- **Pipeline 2**: Focuses on incorporating additional features into the app

---

## 👤 Steps to Add a New IAM User

1. Open the **IAM** section in your AWS Console.  
2. Navigate to **Access Management** and select **Users**.  
3. Click on **Create User**.  
4. Fill in the required details:
   - Provide a unique username  
   - Enable both **programmatic access** and **console access**  
   - Enable the option to require a password reset upon first login  
5. Directly attach policies to the user:
   - Choose **AdministratorAccess**  
6. Click **Next**, then finalize by selecting **Create User**.  
7. Share the login link, username, and temporary password with the new user for AWS Console access.

---

## 🪟 PuTTY Installation (Windows Only)

1. Search for **PuTTY** and download the installer from the official site.  
2. Run the installer and choose the default installation location (preferably the system drive).  
3. Make sure the PATH variable is updated if it's not done automatically.  
4. Launch **PuTTY**:
   - In the **Host Name** field, enter: `ec2-user@<your-EC2-public-IP>`  
   - Go to **SSH > Auth > Credentials**  
   - Browse and select your `.ppk` file (converted from the original `.pem` key)  
5. Hit **Open** to initiate the SSH session.

---

## 💻 Connecting to EC2 via Terminal / PuTTY

Once you're connected to your EC2 instance, execute the following commands to update the system:

```bash
sudo
sudo yum update -y
```
## 🐳 Installing Docker on the EC2 Instance

> Ensure you're still connected to your instance before running the commands below.

### Docker Installation Steps:
```bash
sudo yum update -y
sudo yum install -y docker
sudo systemctl start docker
sudo systemctl enable docker
docker --version
```
### Sample Output:
```bash
[ec2-user@ip-172-31-40-114 ~]$ docker --version
Docker version 25.0.8, build 0bab007
```