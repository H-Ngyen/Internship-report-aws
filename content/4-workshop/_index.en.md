---
title : "Workshop"
date :  "2024-01-01"
weight : 4
chapter : false
pre : " <b> 4. </b> "
---

# Deploy Node.js Application to AWS with Multi-Tier Architecture

#### Overview

Welcome to the workshop on Amazon EC2, DynamoDB, S3, CloudFront, and AWS Lambda!

In this workshop, we will learn and deploy a Node.js application to AWS using a multi-tier architecture. We will explore how to set up VPC networking, deploy EC2 instances, configure DynamoDB database, and deploy serverless email service with Lambda. Afterward, we will apply the learned knowledge by deploying a real-world e-commerce application called CarBuyer on these services.

![](/Internship-report-aws/images/nodejs_x_aws.png)


#### Duration

This workshop may take approximately **90-120 minutes** to complete.

#### Content

1. **[Introduction](4.1-Introduce/)** - Learn about the CarBuyer application (car sales website), overall architecture, and AWS services used in the workshop including EC2, DynamoDB, S3, CloudFront, Lambda.

2. **[Prerequisites](4.2-Prerequiste/)** - Prepare networking infrastructure and access permissions: create VPC with public/private subnets, Internet Gateway, Route Tables, IAM Role for EC2, IAM User and Access Keys for the application.

3. **[Create DynamoDB Database](4.3-database/)** - Create 12 DynamoDB tables for entities such as User, Car, Brand, Color, Type, Material, Accessory, AccessoryType, News, Review, Slider, BookingSchedule. Import sample data into the tables.

4. **[Configure S3 and CloudFront](4.4-storage/)** - Create S3 bucket to store static assets (product images, news, slider). Configure bucket policy for public access. Create CloudFront distribution for content delivery with low latency through global CDN.

5. **[Lambda Email Service](4.5-setup-email-service/)** - Deploy serverless email notification service using AWS Lambda and API Gateway. Configure Lambda function to send confirmation emails for booking schedules and password resets. Create REST API endpoint and configure API Key security.

6. **[Deploy Application to EC2](4.6-deployment/)** - Create Security Groups, initialize 2 EC2 instances (Customer Service in public subnet and Admin/Employee Service in private subnet). Configure NAT Gateway for private subnet. Setup Application Load Balancer with path-based routing and sticky sessions. Deploy Node.js application with PM2 process manager.

7. **[Cleanup Resources](4.7-cleanup/)** - Delete all created AWS resources in the correct order to avoid incurring costs
