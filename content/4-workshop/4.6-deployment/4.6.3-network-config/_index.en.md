---
title : "Setup EC2 Environment"
date :  "2024-01-01" 
weight : 3
chapter : false
pre : " <b> 4.6.3 </b> "
---

### Setup EC2 Environment

In this section, we will connect and configure the environment for the EC2 instances.

#### 1. Create NAT Gateway for Admin Service

1. In **VPC Console**, select **NAT Gateways**
2. Select **Create NAT Gateway**

![](/images/5-workshop/6.deployment/023-nat-gateway.png?width=90pc)

3. Configure NAT Gateway:
   - **Name**: `carbuyer-nat-gateway`
   - **Subnet**: Select **Public Subnet AZ 1b** (carbuyer-fcj-subnet-public2-ap-southeast-1b)
   - **Connectivity type**: Public
   - **Elastic IP allocation ID**: Select **Allocate Elastic IP**
   
4. Select **Create NAT Gateway**

![](/images/5-workshop/6.deployment/026-nat-gateway.png?width=90pc)

5. Update Route Table for Private Subnet AZ 1b:
   - In **VPC Console**, select **Route Tables**
   - Find route table for **Private Subnet AZ 1b** (carbuyer-fcj-rtb-private2-ap-southeast-1b)
   - Select route table → **Routes** tab → **Edit routes**

![](/images/5-workshop/6.deployment/028-route-table.png?width=90pc)

   - **Add route**:
     - **Destination**: `0.0.0.0/0`
     - **Target**: NAT Gateway just created
   - **Save changes**

![](/images/5-workshop/6.deployment/027-route-table.png?width=90pc)

#### 2. Connect to Customer Service Instance

1. In **EC2 Console**, select **Instances**

![](/images/5-workshop/6.deployment/035-connect.png?width=90pc)

2. Select instance `carbuyer-customer-service`, select **Connect**

![](/images/5-workshop/6.deployment/036-connect.png?width=90pc)

3. Select **EC2 Instance Connect** tab

![](/images/5-workshop/6.deployment/038-connect.png?width=90pc)

4. Select **Connect** to open terminal in browser

![](/images/5-workshop/6.deployment/037-connect.png?width=90pc)

#### 3. Install Node.js and PM2

1. Install Node.js 22:

```bash
# Update system
sudo yum update -y
sudo yum install -y git

# Install Node.js 22
curl -fsSL https://rpm.nodesource.com/setup_22.x | sudo bash -
sudo yum install -y nodejs

# Install PM2 globally
sudo npm install -g pm2
```

![](/images/5-workshop/6.deployment/039-node.png?width=90pc)

2. Verify installation:

```bash
node --version
npm --version
pm2 --version
```

![](/images/5-workshop/6.deployment/040-pm2.png?width=90pc)

#### 4. Connect to Admin Service Instance (via Bastion)

1. Copy private key to Customer Service instance:

```bash
# Create .ssh directory if not exists
mkdir -p ~/.ssh
chmod 700 ~/.ssh

# Create private key file (paste content from carbuyer-keypair.pem)
nano ~/.ssh/carbuyer-keypair.pem
chmod 400 ~/.ssh/carbuyer-keypair.pem
```

2. Connect to Admin Service:

```bash
# Get private IP of admin instance from EC2 console
ssh -o StrictHostKeyChecking=accept-new -i ~/.ssh/carbuyer-keypair.pem ec2-user@ADMIN_PRIVATE_IP
```

![](/images/5-workshop/6.deployment/042-bastion.png?width=90pc)

3. Install Node.js and PM2 for Admin Service:

```bash
# Update system
sudo yum update -y
sudo yum install -y git

# Install Node.js 22
curl -fsSL https://rpm.nodesource.com/setup_22.x | sudo bash -
sudo yum install -y nodejs

# Install PM2 globally
sudo npm install -g pm2
```

4. Verify installation:

```bash
node --version
npm --version
pm2 --version
```

![](/images/5-workshop/6.deployment/043-confirm-admin-pm2.png?width=90pc)

Next, we will setup Application Load Balancer