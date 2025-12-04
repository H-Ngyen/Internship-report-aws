---
title : "Create VPC and Network"
date :  "2024-01-01" 
weight : 1 
chapter : false
pre : " <b> 4.2.1. </b> "
---

#### Create VPC and Network

In this step, we will create a VPC with 4 subnets to deploy EC2 instances.

#### Create VPC with Wizard

1. Access **AWS Console** → **VPC**

![](/Internship-report-aws/images/5-workshop/2.prerequisite/001-createvpc.png?width=90pc)

2. Select **Create VPC**

![](/Internship-report-aws/images/5-workshop/2.prerequisite/002-createvpc.png?width=90pc)

3. Configure VPC settings:
   - **Resources to create**: `VPC and more`
   - **Name tag auto-generation**: `carbuyer-fcj`
   - **IPv4 CIDR block**: `10.0.0.0/16`
   - **IPv6 CIDR block**: `No IPv6 CIDR block`

   ![](/Internship-report-aws/images/5-workshop/2.prerequisite/003-createvpc.png?width=90pc)

   - **Tenancy**: `Default`
   - **Number of Availability Zones**: `2`
   - **Number of public subnets**: `2`
   - **Number of private subnets**: `2`

   ![](/Internship-report-aws/images/5-workshop/2.prerequisite/004-createvpc.png?width=90pc)

   - **NAT gateways**: `None`
   - **VPC endpoints**: `S3 Gateway`
   - **DNS options**: Enable DNS hostnames and Enable DNS resolution

   ![](/Internship-report-aws/images/5-workshop/2.prerequisite/005-createvpc.png?width=90pc)

4. Select **Create VPC**

![](/Internship-report-aws/images/5-workshop/2.prerequisite/006-createvpc.png?width=90pc)

4. After successful creation, select **View VPC** to see details

![](/Internship-report-aws/images/5-workshop/2.prerequisite/007-createvpc.png?width=90pc)

![](/Internship-report-aws/images/5-workshop/2.prerequisite/008-createvpc.png?width=90pc)

{{% notice tip %}}
The VPC wizard will automatically create Internet Gateway, S3 Gateway Endpoint, Route Tables and associate subnets. NAT Gateway will be created manually in step 4.6.3.
{{% /notice %}}

#### Create DynamoDB Endpoint

Since VPC wizard only creates S3 Gateway endpoint, we need to create an additional DynamoDB endpoint:

1. Select **Endpoints** → **Create endpoint**

![](/Internship-report-aws/images/5-workshop/2.prerequisite/009-createendpoint.png?width=90pc)

2. Configure:
   - **Name**: `carbuyer-dynamodb-endpoint`
   - **Service category**: AWS services

   ![](/Internship-report-aws/images/5-workshop/2.prerequisite/010-createendpoint.png?width=90pc)

   - **Service name**: `com.amazonaws.ap-southeast-1.dynamodb` (Type: **Gateway**)
   - **VPC**: `carbuyer-fcj-vpc`
   - **Route tables**: Select 3 route tables (skip main route table)

   ![](/Internship-report-aws/images/5-workshop/2.prerequisite/011-createendpoint.png?width=90pc)

3. Select **Create endpoint**

![](/Internship-report-aws/images/5-workshop/2.prerequisite/012-createendpoint.png?width=90pc)

#### Record IPv4 CIDR of Public Subnet

After successfully creating VPC, note the IPv4 CIDR of Public Subnet AZ 1a:

1. In **VPC Console**, select **Subnets**

2. Find and note the IPv4 CIDR of subnet:
   - **Subnet name**: `carbuyer-fcj-subnet-public1-ap-southeast-1a`
   - **IPv4 CIDR**: `10.0.x.x/20` (example: 10.0.0.0/20)

![](/Internship-report-aws/images/5-workshop/2.prerequisite/014-subnet-info.png?width=90pc)

{{% notice info %}}
**Important:** Record the exact IPv4 CIDR of this **Public Subnet AZ 1a**. You will need it to configure Security Group for Admin Service in step 4.6.1.
{{% /notice %}}

Next, we will create an IAM Role for EC2 instances.