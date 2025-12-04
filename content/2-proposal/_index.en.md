---
title : "Project Proposal"
date :  "2025-11-24"
weight : 2
chapter : false
pre : " <b> 2. </b> "
---

## Deploying a Multi-Tier E-commerce Website for Car Sales on AWS

### 1. Project Summary

**CarBuyer** is an e-commerce website specializing in car sales, built entirely on the AWS Cloud with a **Multi-Tier Architecture**. The website provides an online shopping experience for customers and an internal management system for employees and administrators.

**Customers** can easily search and view details of car models, book a test drive, and receive automatic confirmation emails immediately after registration. **Employees** are equipped with comprehensive management tools for products (cars and accessories), appointments, along with the ability to update website content such as news and promotional banners. **Administrators** have the highest level of authority to manage information and accounts for all employees in the system.

The system is designed with a **Multi-Tier Architecture** on AWS, leveraging managed services to ensure flexible scalability, high security, and cost optimization:

- **Amazon EC2** — Runs 2 independent Node.js web services: Customer Service (public subnet) and Admin/Employee Service (private subnet).
- **Amazon VPC** — Network isolation with 2 public subnets and 2 private subnets across 2 Availability Zones.
- **Amazon DynamoDB** — A serverless NoSQL database with 12 tables, auto-scaling on demand.
- **Amazon S3 + CloudFront** — Stores product images and delivers them quickly through a global CDN.
- **AWS Lambda + API Gateway** — Handles sending email notifications (booking confirmation, password reset) in a serverless model.
- **Application Load Balancer** — Intelligently distributes traffic with path-based routing and health checks.

---

### 2. Problem and Solution

#### Current Problem

The original CarBuyer website was developed with MongoDB and stored data files and images locally, leading to the following issues:

- Difficulty in scaling and backing up the database.
- No CDN for fast image distribution.
- Lack of an automated email notification system.
- Significant effort required for infrastructure and database management.

#### Proposed Solution

To address these issues, **CarBuyer** is being migrated to the AWS Cloud with a **Multi-Tier Architecture**, making maximum use of **Managed Services** to reduce operational load and increase performance:

- **DynamoDB** replaces MongoDB — Serverless database, auto-scaling.
- **S3 + CloudFront** — Stores and distributes images via CDN, reducing latency by 60-70%.
- **Lambda + API Gateway** — Sends automated emails (booking confirmation, password reset).
- **VPC** — Network isolation with public/private subnets.
- **Application Load Balancer** — Distributes traffic with path-based routing.
- **EC2** — Runs Node.js/Express.js with PM2 process manager.

---

### Benefits & Return on Investment

- **Reduced Operational Costs** — Saves 35-40% compared to traditional VPS thanks to managed services.
- **80% Reduction in Operational Time** — No need to manage servers, databases, or backups.
- **Improved Performance** — CloudFront CDN reduces latency by up to 60-70%.
- **High Availability** — 24/7 system with Multi-AZ deployment.
- **Automatic Scaling** — DynamoDB auto-scaling, Lambda serverless.
- **Automated Emails** — Lambda sends booking confirmation and password reset emails.

**Estimated Monthly Cost (excluding Free Tier): ≈ $85.54 USD**
**Annual Cost: ≈ $1,026 USD**

### 3. System Architecture

The system is designed based on the **Multi-Tier Architecture** model with 3 independent tiers, making it easy to manage, maintain, and scale:

#### **Application Tier**
- **Node.js/Express.js**: Server-Side Rendering (SSR) handles business logic and renders dynamic HTML on the server.
- **Customer Service** (Public Subnet): Web service for customers, accessible from the internet.
- **Admin/Employee Service** (Private Subnet): Internal management web service, protected by the private subnet.
- **Application Load Balancer**: Distributes traffic between the 2 services with path-based routing.
- **PM2 Process Manager**: Manages and monitors Node.js processes.
- **JWT + Express-session**: Authentication and session management.

#### **Data Tier**
- **Amazon DynamoDB**: 12 NoSQL tables for data storage (User, Car, Brand, Color, Style, FuelType, Accessory, AccessoryType, News, Review, Slider, Appointment).
- **Amazon S3**: Stores product images, news, and sliders.
- **Amazon CloudFront**: CDN for fast image distribution.

#### **Integration Tier**
- **AWS Lambda**: Serverless function for handling email sending (booking confirmation, password reset).
- **Amazon API Gateway**: REST API endpoints with API Key authentication.

![Architecture Overview](/Internship-report-aws/images/arc-log.png)

---

### AWS Services Used

| Category | Service |
|----------|--------|
| **Compute & Networking** | EC2 (2 × t3.micro instances), VPC (2 public + 2 private subnets), Internet Gateway, NAT Gateway, Application Load Balancer |
| **Database & Storage** | DynamoDB (12 tables), S3 (object storage), CloudFront (CDN) |
| **Serverless & Integration** | Lambda (email service), API Gateway (REST API) |
| **Security & Access** | IAM (roles & policies), Security Groups, VPC Gateway Endpoints (S3, DynamoDB) |

---

### 4. Technical Implementation

#### Implementation Phases

The CarBuyer migration project to AWS goes through 4 main phases:

1.  **Architecture Research and Design**: Research AWS services (VPC, EC2, DynamoDB, S3, Lambda, ALB) and design a Multi-Tier architecture suitable for security and scalability requirements. Draw architecture diagrams and identify necessary components.

2.  **Cost Calculation and Feasibility Check**: Use the AWS Pricing Calculator to estimate the costs of services (EC2, ALB, NAT Gateway, DynamoDB, S3, CloudFront, Lambda) to ensure it fits the budget and provides a good return on investment. Evaluate the feasibility of the solution.

3.  **Architecture Adjustment for Cost/Solution Optimization**: Refine the architecture (e.g., using VPC Gateway Endpoints for S3/DynamoDB to reduce NAT Gateway costs, choosing DynamoDB on-demand instead of provisioned) to balance performance and cost.

4.  **Development, Testing, Deployment**: Build the VPC networking, migrate the database from MongoDB to DynamoDB, develop the Lambda email service, deploy Node.js applications to EC2 with PM2, configure ALB and CloudFront, then perform end-to-end testing and go live.

#### Technical Requirements

**Application Layer**: Node.js/Express.js with SSR, PM2 process manager managing 2 services (Customer and Admin/Employee). Uses JWT + express-session for authentication. Frontend HTML/CSS/JavaScript rendered dynamically from the server.

**AWS Infrastructure**: Multi-Tier architecture with VPC (2 public + 2 private subnets across 2 AZs), EC2 t3.micro instances, Application Load Balancer (path-based routing), NAT Gateway, Internet Gateway, Security Groups, IAM roles/policies.

**Data & Storage**: DynamoDB (12 NoSQL tables: User, Car, Brand, Color, Style, FuelType, Accessory, AccessoryType, News, Review, Slider, Appointment), S3 (for image storage), CloudFront CDN (for content delivery), VPC Gateway Endpoints (S3, DynamoDB).

**Serverless Integration**: Lambda function (Nodemailer + Gmail SMTP) handles email notifications (booking confirmation, password reset), API Gateway with REST endpoints and API Key authentication.

**Development Tools**: AWS SDK (@aws-sdk/client-dynamodb, @aws-sdk/client-s3, @aws-sdk/lib-dynamodb), AWS CLI, Git, SSH, Nodemailer.

---

### 5. Roadmap & Milestones

| Month | Outcome |
|-------|--------|
| **Month 1** | Complete learning AWS fundamentals, design architecture. Finalize VPC networking, IAM setup, DynamoDB tables, S3 + CloudFront |
| **Month 2** | Finalize SSR application (Node.js), Lambda email service, API Gateway, EC2 deployment, ALB configuration |
| **Month 3** | Testing, optimization, workshop documentation |
| **End of Month 3** | Deploy to Production |

---

### 6. Cost Estimation

#### AWS Service Costs (estimated for 1,000 - 1,500 active users/month, excluding Free Tier)

| Service | Description | Monthly Cost (USD) |
|---------|-------|--------------------|
| **EC2** | 2 × t3.micro instances (730 hours) | **$20.44** |
| **Application Load Balancer** | 730 hours + LCU charges | **$21.32** |
| **NAT Gateway** | 730 hours + data processing (2GB) | **$43.10** |
| **DynamoDB** | 12 tables, on-demand mode, 1GB storage | **$0.29** |
| **S3 Standard** | 10GB storage + 25K requests | **$0.28** |
| **CloudFront** | CDN distribution, 5GB origin transfer | **$0.10** |
| **Lambda** | Email service (1K requests/month) | **$0.01** |
| **API Gateway** | REST API (1K requests/month) | **$0.00** |

**➡ Total Monthly Cost:** ≈ **$85.54 USD**
**➡ Annual Cost:** ≈ **$1,026 USD**

---

### 7. Risk Assessment

#### Risk Matrix

| Risk | Impact | Probability |
|--------|------------------|----------|
| Cost overruns | Medium | Low |
| Security vulnerabilities | High | Medium |
| Performance issues | Medium | Low |
| Email delivery failures | Low | Medium |

**Mitigation Solutions:**

- Set up CloudWatch billing alerts and AWS Budgets.
- Apply the **principle of least privilege** for IAM roles (grant only the minimum necessary permissions).
- Use restrictive Security Group rules and private subnets.
- Implement retry logic and error logging in Lambda.
- CloudFront CDN and DynamoDB auto-scaling for performance.

---

### 8. Expected Outcomes

#### Technical Outcomes

- A complete e-commerce platform for car sales with a Multi-Tier architecture.
- A secure and scalable system with VPC, Security Groups, ALB, CloudFront.
- Automated email notifications with Lambda and API Gateway.
- 80% reduction in operational time and 35-40% cost savings compared to traditional VPS.

#### Long-term Value

- Demonstrates practical skills in Serverless and DevOps.
- Can be scaled to thousands of users without architectural changes.
- Serves as a standard AWS architecture template that can be reused for future projects.
