---
title : "Prerequisites"
date :  "2024-01-01" 
weight : 2 
chapter : false
pre : " <b> 4.2. </b> "
---

### Prerequisites

In this section, we will prepare the networking infrastructure and access permissions needed to deploy the CarBuyer application to AWS.

#### Requirements

Before starting the workshop, you need:

- **AWS Account** - You can use Free Tier for most services
- **Basic Knowledge** - Understanding of Node.js, networking, and basic AWS concepts
- **Web Browser** - To access AWS Console

#### Overview

We will set up the following foundational resources:

- **Amazon VPC** with 4 subnets (2 public, 2 private) across 2 Availability Zones to ensure high availability
- **Internet Gateway** to allow traffic from internet into public subnets
- **Route Tables** to route traffic between subnets
- **VPC Endpoints** (S3 Gateway and DynamoDB Gateway) to access AWS services without going through the internet
- **IAM Role** for EC2 instances to access DynamoDB and S3
- **IAM User and Access Keys** for Node.js application to use AWS SDK

{{% notice info %}}
NAT Gateway will be created later in step 4.6.3 when needed for private subnet.
{{% /notice %}}

#### Content

1. [Create VPC and Network](4.2.1-create-vpc/)
2. [Create IAM Role for EC2](4.2.2-create-iam-role/)
3. [Create IAM User and Access Keys](4.2.3-create-access-keys/)
