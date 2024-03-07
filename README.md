---

## Hosting a Static Website on AWS

### Overview

The completion of this project was driven by my desire to solidify my theoretical knowledge of AWS core services and their seamless integration. In this project, I demonstrate the deployment of a static HTML web application on AWS, utilizing various AWS services and resources to ensure reliability, security, and scalability. Below is a summary of the resources and configurations utilized in this project:

### Architecture:

- **Virtual Private Cloud (VPC):** Configured a VPC with public and private subnets across two availability zones to enhance availability and fault tolerance.
- **Internet Gateway (IGW):** Deployed an Internet Gateway to facilitate connectivity between VPC instances and the wider Internet.
- **Security Groups:** Act as a network firewall mechanism to control traffic to and from EC2 instances.
- **Availability Zones (AZs):** Leveraged two Availability Zones to enhance system reliability and fault tolerance.
- **Public Subnets:** Used for infrastructure components like the NAT Gateway and Application Load Balancer (ALB).
- **Private Subnets:** For hosting web servers (EC2 instances) for enhanced security.
- **EC2 Instance Connect Endpoint:** For secure connections to assets within both public and private subnets.
- **NAT Gateway:** Enabled instances in private subnets to access the Internet via the NAT Gateway.
- **EC2 Instances:** Hosted the static website on EC2 instances deployed within the private subnets.
- **Application Load Balancer (ALB):** Distributes web traffic to an Auto Scaling Group of EC2 instances across multiple Availability Zones.
- **Auto Scaling Group (ASG):** Manages EC2 instances, ensuring website availability, scalability, fault tolerance, and elasticity.
- **Version Control and Collaboration:** For version control and collaboration.
- **Certificate Manager:** For secured application communications.
- **Simple Notification Service (SNS):** Send email alerts to my preferred email address regarding activities within the Auto Scaling Group.
- **Route 53:** Registered the domain name and set up a DNS A record using Route 53.

### Deployment Script:

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
git clone https://github.com/JoseSoares404/host-a-static-website-on-aws

# Copy all files, including hidden ones, from the cloned repository to the Apache web root
cp -R host-a-static-website-on-aws/. /var/www/html/

# Remove the cloned repository directory to clean up unnecessary files
rm -rf host-a-static-website-on-aws

# Enable the Apache HTTP Server to start automatically at system boot
systemctl enable httpd 

# Start the Apache HTTP Server to serve web content
systemctl start httpd
```

### Repository Link:

[https://github.com/JoseSoares404/host-a-static-website-on-aws](https://github.com/JoseSoares404/host-a-static-website-on-aws)

### Conclusion:

This setup ensures a scalable, secure, and fault-tolerant environment for hosting a static web application, leveraging AWS’ robust infrastructure.
