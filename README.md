# AWS Re-Architecting Project (vProfile Application)

End-to-End Cloud Migration and Re-Architecture using AWS Managed Services, Load Balancing, and Global Content Delivery Network (CloudFront)

## 📌 Project Overview

This project demonstrates the re-architecture of the vProfile application from a traditional infrastructure deployment model to a modern AWS-managed architecture.

The goal was to improve scalability, availability, performance, and operational efficiency by leveraging AWS managed services instead of relying solely on self-managed infrastructure.

The application was deployed using AWS Elastic Beanstalk and integrated with supporting services including Amazon RDS, Amazon ElastiCache (Memcached), Amazon MQ (RabbitMQ), Application Load Balancer (ALB), Auto Scaling, and Amazon CloudFront.

As part of the project, I also performed troubleshooting and root cause analysis to resolve a CloudFront 504 Gateway Timeout error caused by a protocol mismatch between CloudFront and the application origin.

This project provided hands-on experience with cloud architecture design, deployment automation, traffic management, caching, application delivery, and production-style troubleshooting on AWS.

## 🎯 Business Problem

Traditional application deployments often rely on self-managed infrastructure that requires significant operational effort to maintain, scale, secure, and monitor.

As application traffic grows, challenges such as performance bottlenecks, limited scalability, infrastructure management overhead, and global content delivery become increasingly difficult to address.

The objective of this project was to re-architect the vProfile application using AWS managed services to improve operational efficiency, scalability, reliability, and user experience while reducing the burden of infrastructure management.

---
## 🚀 Project Objectives

The key objectives of this project were:

- Deploy the vProfile Java application using AWS Elastic Beanstalk.
- Implement a scalable application architecture using Auto Scaling and Application Load Balancer.
- Migrate supporting services to AWS-managed solutions.
- Integrate Amazon RDS for managed database services.
- Implement Amazon ElastiCache (Memcached) for application caching.
- Integrate Amazon MQ (RabbitMQ) for messaging services.
- Improve application availability and fault tolerance.
- Deliver content globally using Amazon CloudFront.
- Gain hands-on experience with production-style AWS architecture.
- Perform real-world troubleshooting and root cause analysis.

## 🛠️ AWS Services Used

| Service | Purpose |
|----------|----------|
| Amazon Elastic Beanstalk | Application deployment and environment management |
| Amazon EC2 | Compute resources for application hosting |
| Auto Scaling Group (ASG) | Automatic scaling of application instances |
| Application Load Balancer (ALB) | Traffic distribution across application instances |
| Target Group | Routes requests from the ALB to healthy application instances |
| Amazon RDS (MySQL) | Managed relational database service |
| Amazon ElastiCache (Memcached) | In-memory caching layer for improved application performance |
| Amazon MQ (RabbitMQ) | Managed message broker for application communication |
| Amazon CloudFront | Global content delivery network (CDN) |
| Security Groups | Network-level access control and security |

## 🏗️ Solution Architecture

The re-architected vProfile application was deployed using AWS managed services to provide scalability, availability, and improved operational efficiency.

### Architecture Flow

User Request
→ Amazon CloudFront (CDN)
→ Application Load Balancer (ALB)
→ Elastic Beanstalk Environment
→ EC2 Application Instances (Tomcat 10 + Corretto 17)
→ Amazon RDS (MySQL)

Supporting Services:

- Amazon ElastiCache (Memcached) for application caching
- Amazon MQ (RabbitMQ) for messaging and asynchronous communication
- Auto Scaling Group (ASG) for dynamic scaling of application instances
- Security Groups for controlled network access

This architecture enables efficient traffic distribution, improved application performance, reduced latency for global users, and simplified infrastructure management through AWS managed services.

## ⚙️ Project Deployment Workflow

The project was implemented using the following deployment workflow:

### 1. Application Preparation
- Prepared the vProfile Java web application package (.war).
- Verified application dependencies and configuration requirements.

### 2. Elastic Beanstalk Environment Creation
- Created an AWS Elastic Beanstalk environment.
- Selected Tomcat 10 running on Amazon Corretto 17.
- Configured environment settings and application deployment options.

### 3. Database Integration
- Provisioned an Amazon RDS MySQL database.
- Configured database connectivity between the application and RDS.
- Applied security group rules to allow controlled communication.

### 4. Caching Layer Integration
- Provisioned Amazon ElastiCache using Memcached.
- Configured the application to utilize the caching service.

### 5. Messaging Service Integration
- Provisioned Amazon MQ (RabbitMQ).
- Configured messaging services required by the application.

### 6. Traffic Management
- Utilized Application Load Balancer (ALB) and Target Groups.
- Configured health checks and traffic routing.

### 7. Scalability Configuration
- Enabled Auto Scaling to support dynamic workload requirements.
- Verified scaling and load balancing functionality.

### 8. Content Delivery Optimization
- Created an Amazon CloudFront distribution.
- Configured CloudFront to use the Application Load Balancer as the origin.
- Validated global content delivery and application accessibility.

### 9. Validation and Testing
- Verified application functionality.
- Tested application accessibility through CloudFront.
- Confirmed successful communication between all application components.

## 📸 Project Screenshots

### CloudFront Login Page

![CloudFront Login Page](screenshots/01-CloudFront-Login-Page.png)

### CloudFront Distribution

![CloudFront Distribution](screenshots/02-CloudFront-Distribution.png)

### Elastic Beanstalk Environment

![Elastic Beanstalk Environment](screenshots/03-ElasticBeanstalk-Environment.png)

### Deployment Success Events

![Deployment Success Events](screenshots/04-Deployment-Success-Events.png)

### CloudFront Origin Configuration

![CloudFront Origin](screenshots/05-CloudFront-Origin.png)

### Application Load Balancer Listener

![ALB Listener](screenshots/06-ALB-Listener.png)

### Amazon RDS Database

![RDS Database](screenshots/07-RDS-Database.png)


## ⚠️ Troubleshooting & Root Cause Analysis

During the implementation of the CloudFront integration, the application encountered a *504 Gateway Timeout error* when accessed through the CloudFront distribution.

### 🔍 Problem Observed

- The application worked correctly when accessed directly via the Elastic Beanstalk URL.
- However, when accessed through CloudFront, the request failed with a 504 Gateway Timeout error.

### 🧪 Investigation Process

The following components were analyzed during troubleshooting:

- CloudFront distribution configuration
- Origin settings (Elastic Load Balancer)
- Application Load Balancer target group health
- Security group rules
- Protocol configuration between CloudFront and origin

### 🧠 Root Cause

The issue was caused by a *protocol mismatch between CloudFront and the Elastic Load Balancer origin*.

- CloudFront was configured to communicate using HTTPS.
- The origin (ALB/Beanstalk) was serving traffic over HTTP only.

This mismatch prevented CloudFront from successfully establishing a connection to the origin, resulting in a timeout.

### 🛠️ Solution Implemented

- Updated CloudFront origin protocol policy to *HTTP only*
- Ensured ALB listener was correctly configured on port 80 (HTTP)
- Verified target group health checks were passing
- Redeployed CloudFront distribution configuration

### ✅ Result

- CloudFront successfully connected to the origin
- Application became accessible globally through CDN
- 504 Gateway Timeout error was resolved
- Improved application response performance through edge caching


## 📘 Key Learnings

This project provided hands-on experience in designing and deploying a multi-tier cloud architecture on AWS.

Key learnings include:

- Understanding of AWS Elastic Beanstalk for simplified application deployment and management.
- Practical experience with Application Load Balancer (ALB) and Target Groups for traffic distribution.
- Implementation of scalable infrastructure using Auto Scaling Groups.
- Integration of managed AWS services such as RDS, ElastiCache, and Amazon MQ.
- Hands-on experience with CloudFront CDN for global content delivery optimization.
- Real-world troubleshooting of network and protocol-related issues in distributed systems.
- Strengthened understanding of cloud architecture design principles including scalability, availability, and fault tolerance.

- ## 🚀 Conclusion

This project demonstrates a complete end-to-end AWS re-architecture of a traditional web application into a scalable, highly available, and cloud-optimized system.

It highlights practical DevOps skills including cloud deployment, infrastructure configuration, service integration, performance optimization, and troubleshooting.

The experience gained from this project forms a strong foundation for advanced DevOps practices such as CI/CD pipelines, Infrastructure as Code (Terraform/CloudFormation), containerization (Docker), and Kubernetes orchestration.
