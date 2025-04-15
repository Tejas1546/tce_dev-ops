DevOps – Day 2: AWS EC2 Setup & Linux Basics
============================================

🌐 Creating an AWS Account
--------------------------

1.  Visit [AWS Official Site](https://aws.amazon.com/)
    
2.  Click **“Create an AWS Account”**
    
3.  Provide the following details:
    
    *   Email address
        
    *   Password
        
    *   AWS account name
        
4.  Choose **Account Type** – select **Personal** (unless otherwise directed)
    
5.  Add your **billing details** (credit/debit card required)
    
6.  Pick the **Free Basic Plan** under Support Plans
    
7.  Wait for your account to be verified and activated
    

🖥️ Launching an EC2 Instance
-----------------------------

1.  Sign in at the [AWS Console](https://console.aws.amazon.com/)
    
2.  Open the **EC2 Dashboard** by searching “EC2” in the top bar
    
3.  Click **“Launch Instance”**
    
4.  Set up the instance:
    
    *   **Name**: day2-ec2-instance
        
    *   **AMI**: Amazon Linux 2023 or Amazon Linux 2
        
    *   **Instance Type**: t2.micro (eligible for free tier)
        
    *   **Key Pair**: Create and download a new key (e.g., day2-key.pem)
        
    *   **Network Settings**: Allow **SSH (port 22)**
        
5.  Launch the instance
    
6.  After it’s up, go to **Instances > Connect**
    
    *   Choose the **SSH client** tab
        
    *   Copy the SSH command provided for connecting
        

🔌 Connecting to Your EC2 Instance
----------------------------------

Use your terminal and run:

```bash
chmod 400 path/to/day2-key.pem  
ssh -i path/to/day2-key.pem ec2-user@<your-ec2-public-ip>
```
> Replace path/to/day2-key.pem with the actual path to your key file
> Replace with the public IP of your EC2 instance

🔄 Updating Packages on Amazon Linux
------------------------------------

### For Amazon Linux 2:
```bash
sudo yum update -y
```


### For Amazon Linux 2023:

```bash
sudo dnf update -y
```

## 💻 Basic Linux Commands

| Command         | Purpose                                      |
|------------------|----------------------------------------------|
| `ls`             | Lists files and directories                  |
| `pwd`            | Displays the current directory path          |
| `cd <dir>`       | Changes to the specified directory           |
| `touch <file>`   | Creates an empty file                        |
| `mkdir <dir>`    | Creates a new directory                      |
| `rm <file>`      | Deletes a file                               |
| `rmdir <dir>`    | Removes an empty directory                   |
| `sudo`           | Executes a command with superuser privileges |
| `clear`          | Clears the terminal screen                   |
| `exit`           | Exits the SSH session                        |
