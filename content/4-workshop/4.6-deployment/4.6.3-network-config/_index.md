---
title : "Setup EC2 Environment"
date :  "2024-01-01" 
weight : 3
chapter : false
pre : " <b> 4.6.3 </b> "
---

### Setup EC2 Environment

Trong phần này, chúng ta sẽ kết nối và cấu hình môi trường cho các EC2 instances.

### Các bước thực hiện

#### 1. Tạo NAT Gateway cho Admin Service

1. Trong **VPC Console**, chọn **NAT Gateways**
2. Chọn **Create NAT Gateway**

![](/Internship-report-aws/images/5-workshop/6.deployment/023-nat-gateway.png?width=90pc)

3. Cấu hình NAT Gateway:
   - **Name**: `carbuyer-nat-gateway`
   - **Subnet**: Chọn **Public Subnet AZ 1b** (carbuyer-fcj-subnet-public2-ap-southeast-1b)
   - **Connectivity type**: Public
   - **Elastic IP allocation ID**: Chọn **Allocate Elastic IP**
   
4. Chọn **Create NAT Gateway**

![](/Internship-report-aws/images/5-workshop/6.deployment/026-nat-gateway.png?width=90pc)

5. Cập nhật Route Table cho Private Subnet AZ 1b:
   - Trong **VPC Console**, chọn **Route Tables**
   - Tìm route table của **Private Subnet AZ 1b** (carbuyer-fcj-rtb-private2-ap-southeast-1b)
   - Chọn route table → **Routes** tab → **Edit routes**

![](/Internship-report-aws/images/5-workshop/6.deployment/028-route-table.png?width=90pc)

   - **Add route**:
     - **Destination**: `0.0.0.0/0`
     - **Target**: NAT Gateway vừa tạo
   - **Save changes**

![](/Internship-report-aws/images/5-workshop/6.deployment/027-route-table.png?width=90pc)

#### 2. Kết nối Customer Service Instance

1. Trong **EC2 Console**, chọn **Instances**

![](/Internship-report-aws/images/5-workshop/6.deployment/035-connect.png?width=90pc)

2. Chọn instance `carbuyer-customer-service`, chọn **Connect**

![](/Internship-report-aws/images/5-workshop/6.deployment/036-connect.png?width=90pc)

3. Chọn tab **EC2 Instance Connect**

![](/Internship-report-aws/images/5-workshop/6.deployment/038-connect.png?width=90pc)

4. Chọn **Connect** để mở terminal trong browser

![](/Internship-report-aws/images/5-workshop/6.deployment/037-connect.png?width=90pc)

#### 3. Cài đặt Node.js và PM2

1. Cài đặt Node.js 22:

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

![](/Internship-report-aws/images/5-workshop/6.deployment/039-node.png?width=90pc)

2. Kiểm tra cài đặt:

```bash
node --version
npm --version
pm2 --version
```

![](/Internship-report-aws/images/5-workshop/6.deployment/040-pm2.png?width=90pc)

#### 4. Kết nối Admin Service Instance (qua Bastion)

1. Copy private key vào Customer Service instance:

```bash
# Tạo thư mục .ssh nếu chưa có
mkdir -p ~/.ssh
chmod 700 ~/.ssh

# Tạo file private key (paste nội dung từ carbuyer-keypair.pem)
nano ~/.ssh/carbuyer-keypair.pem
chmod 400 ~/.ssh/carbuyer-keypair.pem
```

2. Kết nối đến Admin Service:

```bash
# Lấy private IP của admin instance từ EC2 console
ssh -o StrictHostKeyChecking=accept-new -i ~/.ssh/carbuyer-keypair.pem ec2-user@ADMIN_PRIVATE_IP
```

![](/Internship-report-aws/images/5-workshop/6.deployment/042-bastion.png?width=90pc)

3. Cài đặt Node.js và PM2 cho Admin Service:

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

4. Kiểm tra cài đặt:

```bash
node --version
npm --version
pm2 --version
```

![](/Internship-report-aws/images/5-workshop/6.deployment/043-confirm-admin-pm2.png?width=90pc)

Tiếp theo, chúng ta sẽ setup Application Load Balancer