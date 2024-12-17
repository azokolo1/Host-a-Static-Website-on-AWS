# Host a Static Website on AWS

## Project Overview
This project demonstrates hosting a static HTML web app on AWS using various cloud resources and services. The deployment is managed through an automated setup script and follows best practices for security, scalability, and fault tolerance.

## Architecture Summary
The architecture includes the following key components:

1. **Virtual Private Cloud (VPC):** Configured with public and private subnets across two Availability Zones (AZs).
2. **Internet Gateway:** Facilitates connectivity between VPC instances and the Internet.
3. **Security Groups:** Act as network firewalls to control inbound and outbound traffic.
4. **Availability Zones:** Enhance reliability and fault tolerance by leveraging multiple AZs.
5. **Public Subnets:** Used for the NAT Gateway and Application Load Balancer.
6. **EC2 Instance Connect Endpoint:** Allows secure connections to instances within public and private subnets.
7. **Private Subnets:** Host web servers (EC2 instances) for better security.
8. **NAT Gateway:** Enables instances in private subnets to access the Internet securely.
9. **EC2 Instances:** Host the web application.
10. **Application Load Balancer:** Distributes incoming web traffic evenly across EC2 instances in an Auto Scaling Group.
11. **Auto Scaling Group:** Manages EC2 instances automatically for availability, scalability, fault tolerance, and elasticity.
12. **GitHub Repository:** Stores web files for version control and collaboration.
13. **Certificate Manager:** Secures application communications.
14. **Simple Notification Service (SNS):** Sends alerts for Auto Scaling Group activities.
15. **Route 53:** Manages domain name registration and DNS records.

## Deployment Steps
1. Launch an EC2 instance with Amazon Linux.
2. Use the following setup script to configure the server:

```bash
#!/bin/bash
# Switch to root user
sudo su

# Update all packages
yum update -y

# Install Apache HTTP Server
yum install -y httpd

# Navigate to Apache web root
cd /var/www/html

# Install Git
yum install git -y

# Clone project repository from GitHub
git clone https://github.com/azokolo1/Host-a-Static-Website-on-AWS.git

# Copy files to Apache web root
cp -R Host-a-Static-Website-on-AWS/. /var/www/html/

# Remove cloned repository
delete Host-a-Static-Website-on-AWS

# Enable Apache to start on boot
systemctl enable httpd

# Start Apache
systemctl start httpd
```

## Repository Structure
- **Reference Diagram:** A visual representation of the architecture.
- **Deployment Scripts:** Scripts used to deploy the web application.

## How to Access the Application
- Register a domain name using Route 53.
- Configure DNS records pointing to the Application Load Balancer.
- Access the web application through the registered domain name.

---
Feel free to explore the repository for more detailed scripts and configuration files.

