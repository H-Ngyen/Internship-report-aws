---
title : "Deploy Application to EC2"
date :  "2024-01-01" 
weight : 6
chapter : false
pre : " <b> 4.6. </b> "
---

### Deploy Application to EC2

In this section, we will deploy the CarBuyer application to Amazon EC2 instances with 2 separate services.

#### Introduction to Amazon EC2

Amazon EC2 (Elastic Compute Cloud) provides scalable virtual servers in the cloud, allowing you to run applications with flexible configuration.

**Key Advantages:**

- **Flexible** - Many instance types with different CPU, memory, storage configurations
- **Scalable** - Easy to scale up/down based on demand
- **Cost-effective** - Pay only for actual compute capacity used
- **Secure** - Security Groups and Network ACLs to control traffic
- **Reliable** - Deploy across multiple Availability Zones for high availability

#### Introduction to Application Load Balancer

Application Load Balancer (ALB) operates at layer 7 (application layer), distributing incoming traffic to multiple targets like EC2 instances.

**Key Advantages:**

- **Path-based Routing** - Route requests based on URL path
- **Health Checks** - Automatically checks target health and routes only to healthy instances
- **SSL/TLS Termination** - Handles HTTPS connections
- **High Availability** - Automatically distributes traffic across multiple Availability Zones
- **Integration** - Works well with Auto Scaling, CloudWatch, and other AWS services

#### Deployment Architecture

In this workshop, we will deploy 2 separate Node.js applications:

1. **Customer Service** (Public subnet):
   - EC2 instance running Node.js application
   - Serves customers: view cars, schedule test drives, buy accessories
   - Accessible from internet via Application Load Balancer
   - Connects to DynamoDB via VPC Gateway Endpoint

2. **Admin/Employee Service** (Private subnet):
   - EC2 instance running Node.js application
   - Internal management: CRUD cars, accessories, news, orders, customers
   - Accessible via ALB (for admin) or SSH (for employees)
   - Connects to internet via NAT Gateway to download packages
   - Connects to DynamoDB via VPC Gateway Endpoint

3. **Application Load Balancer**:
   - Distributes traffic to both EC2 instances
   - Health checks to ensure availability
   - Path-based routing: `/` → Customer Service, `/admin` → Admin Service

4. **NAT Gateway**:
   - Allows Admin Service (private subnet) to access internet
   - Required for downloading npm packages and system updates

5. **VPC Gateway Endpoints**:
   - DynamoDB endpoint: Access DynamoDB without internet
   - S3 endpoint: Upload/download media files from S3

#### Content

1. [Create Security Groups](4.6.1-create-security-groups/)
2. [Create EC2 Instances](4.6.2-create-ec2/)
3. [Configure Network](4.6.3-network-config/)
4. [Setup Application Load Balancer](4.6.4-setup-alb/)
5. [Deploy Applications](4.6.5-deploy-apps/)
6. [Test Application](4.6.6-test-application/)