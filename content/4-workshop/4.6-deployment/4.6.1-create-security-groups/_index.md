---
title : "Tạo Security Groups"
date :  "2024-01-01" 
weight : 1
chapter : false
pre : " <b> 4.6.1 </b> "
---

#### Tạo Security Groups

Trong bước này, chúng ta sẽ tạo các Security Groups để kiểm soát traffic cho 2 EC2 instances.

#### 1. Tạo Security Group cho Customer Service

1. Truy cập **EC2 Console** → **Security Groups**
2. Chọn **Create security group**

![](/images/5-workshop/6.deployment/001-securitygroups.png?width=90pc)

#### Cấu hình cơ bản:
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
- **All traffic** (0.0.0.0/0) - Mặc định

3. Chọn **Create security group**

![](/images/5-workshop/6.deployment/005-createcustomersg.png?width=90pc)

#### 2. Tạo Security Group cho Admin Service

{{% notice tip %}}
**Ghi chú:** Sử dụng IPv4 CIDR của Public Subnet AZ 1a đã ghi chú từ bước 4.2.1 thay vì `10.0.1.0/24`.
{{% /notice %}}

1. Chọn **Create security group**

![](/images/5-workshop/6.deployment/001-securitygroups.png?width=90pc)

#### Cấu hình cơ bản:
- **Name**: `carbuyer-admin-sg`
- **Description**: `Security group for admin service EC2`
- **VPC**: `carbuyer-fcj-vpc`

#### Inbound Rules:
| Type | Protocol | Port | Source | Description |
|------|----------|------|--------|-------------|
| SSH | TCP | 22 | 10.0.1.0/24 | SSH access from Customer EC2 |

![](/images/5-workshop/6.deployment/007-adminsecuritygroup.png?width=90pc)

#### Outbound Rules:
- **All traffic** (0.0.0.0/0) - Cho phép internet access qua NAT Gateway

2. Chọn **Create security group**

![](/images/5-workshop/6.deployment/008-createadminsg.png?width=90pc)

#### Kiểm tra kết quả

Sau khi hoàn thành, bạn sẽ có các Security Groups:

- ✅ `carbuyer-customer-sg` - Customer service trong Public Subnet
- ✅ `carbuyer-admin-sg` - Admin service trong Private Subnet

Tiếp theo, chúng ta sẽ tạo EC2 instance cho Customer Service.