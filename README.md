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
