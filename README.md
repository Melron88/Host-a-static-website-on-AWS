![Alt text](/Host_a_Static_Website_on_AWS (1).png)

# Hosting a Static Website on AWS

This project involves hosting a static HTML web application on Amazon Web Services (AWS) utilizing various resources and configurations to ensure reliability, security, and scalability.

## Overview

The project utilizes the following AWS resources and configurations:

1. **Virtual Private Cloud (VPC)**: Configured with public and private subnets across multiple availability zones to isolate resources and enhance fault tolerance.
   
2. **Internet Gateway**: Deployed to facilitate connectivity between VPC instances and the wider Internet.

3. **Security Groups**: Utilized as a network firewall mechanism to control traffic to EC2 instances.

4. **Availability Zones**: Leveraged to enhance system reliability and fault tolerance by distributing resources across multiple zones.

5. **Public Subnets**: Utilized for infrastructure components like the NAT Gateway and Application Load Balancer to enable internet access.

6. **EC2 Instance Connect Endpoint**: Implemented for secure connections to assets within both public and private subnets.

7. **Private Subnets**: Web servers (EC2 instances) positioned within private subnets for enhanced security.

8. **NAT Gateway**: Enabled instances in private subnets to access the Internet while remaining private.

9. **Hosting on EC2 Instances**: The website is hosted on EC2 instances.

10. **Application Load Balancer (ALB)**: Used for evenly distributing web traffic to an Auto Scaling Group of EC2 instances across multiple Availability Zones.

11. **Auto Scaling Group**: Automatically manages EC2 instances, ensuring website availability, scalability, fault tolerance, and elasticity.

12. **Version Control**: Web files stored on GitHub for version control and collaboration.

13. **Certificate Manager**: Application communications secured using SSL/TLS certificates.

14. **Simple Notification Service (SNS)**: Configured to alert about activities within the Auto Scaling Group.

15. **Route 53**: Domain name registered and DNS records set up using Route 53.

## Deployment Script

The following script can be used to deploy the static website on an EC2 instance:

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

## Instructions

1. **AWS Configuration**: Set up the VPC, Internet Gateway, Security Groups, Subnets, NAT Gateway, ALB, Route 53, and other necessary resources according to the provided configuration.

2. **EC2 Instance**: Launch an EC2 instance within the configured VPC and subnet. Use the provided deployment script to set up Apache HTTP Server and clone the project from GitHub.

3. **Auto Scaling Group**: Configure an Auto Scaling Group with the EC2 instance to ensure availability and scalability.

4. **Route 53**: Register a domain name and set up DNS records to point to the ALB for accessing the website.

5. **Testing**: Test the website to ensure proper functionality.

For detailed instructions on setting up each component, refer to AWS documentation or consult with your DevOps team.

---


