![Alt test](/Host_a_Static_Website_on_AWS.png)

---

# Hosting a Static Website on AWS

This repository contains resources and scripts used to deploy a static HTML web app on AWS. The setup includes a variety of AWS services to ensure high availability, scalability, and security for the hosted web app.

## Project Overview

In this project, we utilized AWS services to host a static website, leveraging best practices in cloud architecture to ensure reliability, security, and scalability. The following AWS resources and configurations were employed:

- **Virtual Private Cloud (VPC) Configuration:** Configured a VPC with public and private subnets across two Availability Zones (AZs) to enhance fault tolerance and security.
- **Internet Connectivity:** Deployed an Internet Gateway to facilitate connectivity between the VPC instances and the Internet.
- **Security:** Established Security Groups to act as a network firewall mechanism, controlling inbound and outbound traffic.
- **Availability Zones:** Used two Availability Zones to ensure high availability and fault tolerance.
- **Public Subnets:** Utilized public subnets for infrastructure components such as the NAT Gateway and Application Load Balancer.
- **Private Subnets:** Positioned web servers (EC2 instances) within private subnets for enhanced security.
- **EC2 Instances:** Hosted the website on EC2 Instances within private subnets.
- **Load Balancing and Auto Scaling:**
   - Implemented an Application Load Balancer and a target group to distribute web traffic across an Auto Scaling Group of EC2 instances.
   - Configured an Auto Scaling Group to manage EC2 instances automatically, ensuring scalability and fault tolerance.
- **Version Control and Deployment:** Stored web files in a GitHub repository for version control and collaboration.
- **Security Certificates:** Secured application communications using AWS Certificate Manager.
- **Notifications:** Configured Simple Notification Service (SNS) for alerts related to Auto Scaling Group activities.
- **Domain Registration and DNS:** Registered a domain name and set up DNS records using Route 53.

## Deployment Script
```bash
#!/bin/bash
# Switch to the root user to gain full administrative privileges
sudo su
# Update all installed packages to their latest versions
yum update -y
# Install Apache HTTP Server
yum install -y httpd
# Change the current working directory to the Apache web root
cd /var/www/html
# Install Git
yum install git -y
# Clone the project GitHub repository to the current directory
git clone https://github.com/aosnotes77/host-a-static-website-on-aws.git
# Copy all files, including hidden ones, from the cloned repository to the Apache web root
cp -R host-a-static-website-on-aws/. /var/www/html/
# Remove the cloned repository directory to clean up unnecessary files
rm -rf host-a-static-website-on-aws
# Enable the Apache HTTP Server to start automatically at system boot
systemctl enable httpd
# Start the Apache HTTP Server to serve web content
systemctl start httpd
```

## Getting Started

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/ebenezerbabatop/host-a-static-website-on-aws.git
   ```

2. **Deploy the Web Application:**
   - Follow the provided bash script to set up the EC2 instance and deploy the static website.

3. **Access the Website:**
   - After deployment, access your website via the public domain name registered with Route 53.
