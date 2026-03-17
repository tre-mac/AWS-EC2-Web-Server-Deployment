# AWS-EC2-Web-Server-Deployment

Project Summary

In this project, I deployed and managed a cloud-based web server using Amazon EC2. The goal was to understand how cloud infrastructure works from start to finish including deployment, security, monitoring, scaling, and protection mechanisms.
_______________________________________________________________________________________________
Launching the EC2 Instance

- Selected Amazon EC2 (IaaS) in AWS

AMI: Amazon Linux 2023

Instance Type: t2.micro

- Created a key pair for secure SSH access

Enabled:

✅ Termination Protection

✅ Stop Protection

This ensures the server is secure and prevents accidental deletion early on.
___________________________________________________________________________________________________
Automating the Web Server Setup

- Instead of manually installing software, I used a User Data script:

#!/bin/bash
dnf install -y httpd
systemctl enable httpd
systemctl start httpd
echo '<html><h1>Hello From My Web Server!</h1></html>' > /var/www/html/index.html

What this does:

Installs Apache

Starts the web server

Creates a live webpage automatically

Server was ready immediately after launch
________________________________________________________________________________________________________
Configuring Network Security

At first, the server did NOT load in the browser because the security group (firewall) had no inbound rules

Added rule:

HTTP (Port 80) → Anywhere (IPv4)

Web server became accessible via public IP

Key takeaway:
Cloud servers are secure by default, so you must explicitly allow traffic.
___________________________________________________________________________________________________________
Monitoring the Instance

- Used EC2 Status Checks

System status ✅

Instance status ✅

- Viewed metrics in CloudWatch

Why this matters:
Monitoring ensures reliability and helps detect failures early.
_____________________________________________________________________________________________________________
Scaling the Server

- To simulate real-world demand, I upgraded resources:

Stopped the instance

Changed:

Instance: t2.micro → t2.small

Storage: 8 GiB → 10 GiB

Improved performance capacity

Key concept:
Cloud allows on-demand scaling without rebuilding infrastructure.
_________________________________________________________________________________________________________________
What I Learned

How to deploy a server in the cloud from scratch

Importance of security groups (firewalls)

How to automate infrastructure using scripts

How cloud scaling works in real scenarios

Why protection mechanisms are critical in production

How to manage cost by cleaning up resources



