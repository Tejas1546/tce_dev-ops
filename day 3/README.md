# DevOps – Day 3: IAM, EC2, CI/CD & Docker Setup

## 🔐 AWS IAM User Role

### User Details:
- **User Name**:  
- **Console Password**:  

---

## 🚀 AWS EC2 – Launch Instance

1. Login to AWS Console.  
2. Search for **EC2** and go to **EC2 Dashboard**.  
3. Click on **Launch Instance**.  
4. Configure the instance:
   - Choose AMI: **Amazon Linux**
   - Instance Type: `t2.micro`
   - Key pair: create/download key
   - Enable **SSH (port 22)** in network settings  
5. Launch the instance.  

---

## 🔁 CI/CD Pipeline

### CI/CD Flow:
```bash
START -> INSTANCE (AWS LINUX) -> DEV -> POLICY (CI) -> EC2 INSTANCE -> Deploying the application -> END
```
### Micro Pipelines:

- **Pipeline 2**: Adding more features

---

## 👤 Creating a New IAM User

1. Go to **IAM** in AWS Console.  
2. Under **Access Management**, select **Users**.  
3. Click **Create User**.  
4. Enter:
   - Name  
   - **User access**: ✅ checked  
   - Require password reset on first login: ✅ checked  
5. Attach policies directly:
   - ✅ **AdministratorAccess**  
6. Click **Next**, then **Create User**.  
7. Use the Console Sign-in link, user name, and password to log in as the new IAM user.

---

## 🪟 Download PuTTY (For Windows Users)

1. Search for **PuTTY** in Google.  
2. Download and install it.  
3. Save it in the **hard drive** (Option 2 in installer dropdown).  
4. Set environment variable path (if not set automatically).  
5. Open **PuTTY**:
   - **Host Name**: `ec2-user@<EC2_PUBLIC_IP>`  
   - Go to **SSH > Auth > Credentials**:
     - Browse and select the `.ppk` file (converted from your `.pem` key)  
6. Click **Open** to start the session.

---

## 💻 EC2 Console / PuTTY Interface

Once connected, run:

```bash
sudo
sudo yum update -y
```

## 🐳 Download & Install Docker
> Make sure PuTTY session is active before running these commands.
## Docker Installation Steps:
```bash
sudo yum update -y
sudo yum install -y docker
sudo systemctl start docker
sudo systemctl enable docker
docker --version
```
## Expected Output (Example):
```bash
[ec2-user@ip-172-31-40-114 ~]$ docker --version
Docker version 25.0.8, build 0bab007
```
