# Project 1 – Install & Configure Webserver on EC2

## Overview
In this project, I launched an Amazon EC2 instance using Amazon Linux 2 and configured a web server on it. I installed Apache (with an option to use Nginx) and deployed a simple HTML page that can be accessed publicly using the instance’s public IP address.

This project helped me understand how EC2, security groups, and basic Linux server configuration work together in a real-world setup.

---

## Services and Tools Used
- Amazon EC2
- Amazon Linux 2
- Apache HTTP Server (httpd)
- Nginx (optional)
- AWS Security Groups
- SSH (Terminal)

---

## What I Did

### 1. Launched an EC2 Instance
I created an EC2 instance from the AWS Management Console with the following configuration:
- AMI: Amazon Linux 2 (Free Tier eligible)
- Instance type: t2.micro
- Key pair: Created a new key pair and downloaded the `.pem` file
- Security Group:
  - Allowed SSH (port 22) only from my IP
  - Allowed HTTP (port 80) from anywhere

Once the instance was launched, I noted down the public IP address.

---

### 2. Connected to the EC2 Instance
Using the downloaded key pair, I connected to the EC2 instance from my local terminal using SSH.
```
ssh -i "keyname.pem" ec2-user@<Public_IP>
```
---

3. Installed and Configured the Web Server

I updated the system packages and installed the Apache web server. After installation, I started the service and enabled it so that it runs automatically on system reboot.
```
sudo yum update -y
sudo yum install -y httpd
sudo systemctl start httpd
sudo systemctl enable httpd
```

(Alternatively, Nginx can also be installed using Amazon Linux Extras.)

4. Deployed a Simple HTML Page

To verify the web server setup, I created a basic HTML page and placed it in the default web root directory.
```
echo "<h1>Welcome to my Webserver on AWS!</h1>" | sudo tee /var/www/html/index.html
```
I verified that the file was created correctly:
```
cat /var/www/html/index.html
```
5. Verified the Web Server

Finally, I opened a browser and accessed the application using the public IP address of the EC2 instance.
```
http://<Public_IP>
```

The welcome message displayed successfully, confirming that the web server was running and publicly accessible.
