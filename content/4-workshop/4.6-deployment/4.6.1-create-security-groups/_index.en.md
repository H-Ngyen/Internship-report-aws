---
title : "Create Security Groups"
date :  "2024-01-01" 
weight : 1
chapter : false
pre : " <b> 4.6.1 </b> "
---

#### Create Security Groups

In this step, we will create Security Groups to control traffic for 2 EC2 instances.

#### 1. Create Security Group for Customer Service

1. Access **EC2 Console** → **Security Groups**
2. Select **Create security group**

![](/images/5-workshop/6.deployment/001-securitygroups.png?width=90pc)

#### Basic Configuration:
- **Name**: `carbuyer-customer-sg`
- **Description**: `Security group for customer service EC2`
- **VPC**: `carbuyer-fcj-vpc`

![](/images/5-workshop/6.deployment/002-customersecuritygroup.png?width=90pc)

#### Inbound Rules:
| Type | Protocol | Port | Source | Description |
|------|----------|------|--------|-------------|
| SSH | TCP | 22 | 0.0.0.0/0 | SSH access |

![](/images/5-workshop/6.deployment/004-customerinboundrules.png?width=90pc)

#### Outbound Rules:
- **All traffic** (0.0.0.0/0) - Default

3. Select **Create security group**

![](/images/5-workshop/6.deployment/005-createcustomersg.png?width=90pc)

#### 2. Create Security Group for Admin Service

{{% notice tip %}}
**Note:** Use the IPv4 CIDR of Public Subnet AZ 1a noted from step 4.2.1 instead of `10.0.1.0/24`.
{{% /notice %}}

1. Select **Create security group**

![](/images/5-workshop/6.deployment/001-securitygroups.png?width=90pc)

#### Basic Configuration:
- **Name**: `carbuyer-admin-sg`
- **Description**: `Security group for admin service EC2`
- **VPC**: `carbuyer-fcj-vpc`

#### Inbound Rules:
| Type | Protocol | Port | Source | Description |
|------|----------|------|--------|-------------|
| SSH | TCP | 22 | 10.0.1.0/24 | SSH access from Customer EC2 |

![](/images/5-workshop/6.deployment/007-adminsecuritygroup.png?width=90pc)

#### Outbound Rules:
- **All traffic** (0.0.0.0/0) - Allow internet access via NAT Gateway

2. Select **Create security group**

![](/images/5-workshop/6.deployment/008-createadminsg.png?width=90pc)

#### Verify Results

After completion, you will have the Security Groups:

- ✅ `carbuyer-customer-sg` - Customer service in Public Subnet
- ✅ `carbuyer-admin-sg` - Admin service in Private Subnet

Next, we will create an EC2 instance for Customer Service.