---
title : "Create EC2 Instances"
date :  "2024-01-01" 
weight : 2
chapter : false
pre : " <b> 4.6.2 </b> "
---

### Create EC2 Instances

In this section, we will create 2 EC2 instances for Customer Service and Admin/Employee Service.

### Steps

#### 1. Create EC2 Instance for Customer Service

1. Access **EC2 Console** at [EC2 Dashboard](https://console.aws.amazon.com/ec2/)
2. Select **Launch an instance**

![](/images/5-workshop/6.deployment/002-ec2.png?width=90pc)

#### Name and tags:
- **Name**: `carbuyer-customer-service`

![](/images/5-workshop/6.deployment/003-ec2.png?width=90pc)

#### Application and OS Images (Amazon Machine Image):
- Select **Amazon Linux 2023 AMI**
- **Architecture**: Select 64-Bit (x86)

![](/images/5-workshop/6.deployment/004-ec2.png?width=90pc)

#### Instance type:
- Select **t2.micro** (Free tier eligible)
- 1 vCPU, 1 GiB Memory

#### Key pair (login):
- **Key pair name**: `carbuyer-keypair` (or create new if not exists)
- **Key pair type**: RSA
- **Private key file format**: .pem

![](/images/5-workshop/6.deployment/005-ec2.png?width=90pc)

#### Network settings:
Select **Edit** to configure:
- **Network (VPC)**: `carbuyer-fcj-vpc`
- **Subnet**: Select **Public Subnet AZ 1a** (10.0.0.0/20)
- **Auto-assign public IP**: Enable
- **Firewall (security groups)**: Select existing security group → `carbuyer-customer-sg`

![](/images/5-workshop/6.deployment/007-ec2.png?width=90pc)

#### Configure storage:
- Keep default: 8 GiB gp3 (Free tier eligible)

#### Advanced details:
- **IAM instance profile**: `carbuyer-ec2-role`
3. Select **Launch instance**

![](/images/5-workshop/6.deployment/008-ec2.png?width=90pc)

#### 2. Create EC2 Instance for Admin/Employee Service

1. Select **Launch an instance** again

![](/images/5-workshop/6.deployment/009-ec2.png?width=90pc)

2. Use the same configuration as Customer Service but change:

#### Name and tags:
- **Name**: `carbuyer-admin-service`

![](/images/5-workshop/6.deployment/010-ec2.png?width=90pc)

#### Network settings (Edit):
- **Network (VPC)**: `carbuyer-fcj-vpc`
- **Subnet**: Select **Private Subnet AZ 1b** (10.0.3.0/24)
- **Auto-assign public IP**: Disable
- **Firewall (security groups)**: Select existing security group → `carbuyer-admin-sg`

![](/images/5-workshop/6.deployment/012-ec2.png?width=90pc)

3. Keep other configurations unchanged (AMI, instance type, key pair, IAM role)

4. Select **Launch instance**

![](/images/5-workshop/6.deployment/013-ec2.png?width=90pc)

#### 3. Verify instances

1. In **EC2 Console**, select **Instances** from the left menu

![](/images/5-workshop/6.deployment/014-ec2.png?width=90pc)

2. Confirm both instances are in **Running** state:
   - `carbuyer-customer-service` - Public subnet, has Public IP
   - `carbuyer-admin-service` - Private subnet, only has Private IP

3. Verify information:
   - **Instance State**: Running
   - **Status Check**: 2/2 checks passed
   - **Security Groups**: Correct security group assigned
   - **IAM Role**: carbuyer-ec2-role

### Verify Results

After completion, you will have:

- ✅ EC2 Customer Service instance in public subnet
- ✅ EC2 Admin Service instance in private subnet  
- ✅ Both instances have IAM role `carbuyer-ec2-role`
- ✅ Security groups configured correctly
- ✅ Instances ready to install applications

Next, we will setup the environment for the instances.