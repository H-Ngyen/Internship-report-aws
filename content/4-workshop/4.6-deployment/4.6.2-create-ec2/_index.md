---
title : "Tạo EC2 Instances"
date :  "2024-01-01" 
weight : 2
chapter : false
pre : " <b> 4.6.2 </b> "
---

### Tạo EC2 Instances

Trong phần này, chúng ta sẽ tạo 2 EC2 instances cho Customer Service và Admin/Employee Service.

### Các bước thực hiện

#### 1. Tạo EC2 Instance cho Customer Service

1. Truy cập **EC2 Console** tại [EC2 Dashboard](https://console.aws.amazon.com/ec2/)
2. Chọn **Launch an instance**

![](/Internship-report-aws/images/5-workshop/6.deployment/002-ec2.png?width=90pc)

#### Name and tags:
- **Name**: `carbuyer-customer-service`

![](/Internship-report-aws/images/5-workshop/6.deployment/003-ec2.png?width=90pc)

#### Application and OS Images (Amazon Machine Image):
- Chọn **Amazon Linux 2023 AMI**
- **Architecture**: Chọn 64-Bit (x86)

![](/Internship-report-aws/images/5-workshop/6.deployment/004-ec2.png?width=90pc)

#### Instance type:
- Chọn **t2.micro** (Free tier eligible)
- 1 vCPU, 1 GiB Memory

#### Key pair (login):
- **Key pair name**: `carbuyer-keypair` (hoặc tạo mới nếu chưa có)
- **Key pair type**: RSA
- **Private key file format**: .pem

![](/Internship-report-aws/images/5-workshop/6.deployment/005-ec2.png?width=90pc)

#### Network settings:
Chọn **Edit** để cấu hình:
- **Network (VPC)**: `carbuyer-fcj-vpc`
- **Subnet**: Chọn **Public Subnet AZ 1a** (10.0.0.0/20)
- **Auto-assign public IP**: Enable
- **Firewall (security groups)**: Select existing security group → `carbuyer-customer-sg`

![](/Internship-report-aws/images/5-workshop/6.deployment/007-ec2.png?width=90pc)

#### Configure storage:
- Giữ mặc định: 8 GiB gp3 (Free tier eligible)

#### Advanced details:
- **IAM instance profile**: `carbuyer-ec2-role`
3. Chọn **Launch instance**

![](/Internship-report-aws/images/5-workshop/6.deployment/008-ec2.png?width=90pc)

#### 2. Tạo EC2 Instance cho Admin/Employee Service

1. Chọn **Launch an instance** một lần nữa

![](/Internship-report-aws/images/5-workshop/6.deployment/009-ec2.png?width=90pc)

2. Sử dụng cùng cấu hình như Customer Service nhưng thay đổi:

#### Name and tags:
- **Name**: `carbuyer-admin-service`

![](/Internship-report-aws/images/5-workshop/6.deployment/010-ec2.png?width=90pc)

#### Network settings (Edit):
- **Network (VPC)**: `carbuyer-fcj-vpc`
- **Subnet**: Chọn **Private Subnet AZ 1b** (10.0.3.0/24)
- **Auto-assign public IP**: Disable
- **Firewall (security groups)**: Select existing security group → `carbuyer-admin-sg`

![](/Internship-report-aws/images/5-workshop/6.deployment/012-ec2.png?width=90pc)

3. Giữ nguyên các cấu hình khác (AMI, instance type, key pair, IAM role)

4. Chọn **Launch instance**

![](/Internship-report-aws/images/5-workshop/6.deployment/013-ec2.png?width=90pc)

#### 3. Kiểm tra instances

1. Trong **EC2 Console**, chọn **Instances** từ menu bên trái

![](/Internship-report-aws/images/5-workshop/6.deployment/014-ec2.png?width=90pc)

2. Xác nhận cả 2 instances đang ở trạng thái **Running**:
   - `carbuyer-customer-service` - Public subnet, có Public IP
   - `carbuyer-admin-service` - Private subnet, chỉ có Private IP

3. Kiểm tra các thông tin:
   - **Instance State**: Running
   - **Status Check**: 2/2 checks passed
   - **Security Groups**: Đúng security group đã được gán
   - **IAM Role**: carbuyer-ec2-role

### Kiểm tra kết quả

Sau khi hoàn thành, bạn sẽ có:

- ✅ EC2 Customer Service instance trong public subnet
- ✅ EC2 Admin Service instance trong private subnet  
- ✅ Cả 2 instances đều có IAM role `carbuyer-ec2-role`
- ✅ Security groups được cấu hình đúng
- ✅ Các instances sẵn sàng để cài đặt ứng dụng

Tiếp theo, chúng ta sẽ setup môi trường cho các instances.