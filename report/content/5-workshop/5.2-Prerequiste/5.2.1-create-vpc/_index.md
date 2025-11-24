---
title : "Tạo VPC và Network"
date :  "2024-01-01" 
weight : 1 
chapter : false
pre : " <b> 5.2.1. </b> "
---

#### Tạo VPC và Network

Trong bước này, chúng ta sẽ tạo VPC với 4 subnets để triển khai EC2 instances.

#### Tạo VPC với Wizard

1. Truy cập **AWS Console** → **VPC**

![](/images/5-workshop/2.prerequisite/001-createvpc.png?width=90pc)

2. Chọn **Create VPC**

![](/images/5-workshop/2.prerequisite/002-createvpc.png?width=90pc)

3. Cấu hình VPC settings:
   - **Resources to create**: `VPC and more`
   - **Name tag auto-generation**: `carbuyer-fcj`
   - **IPv4 CIDR block**: `10.0.0.0/16`
   - **IPv6 CIDR block**: `No IPv6 CIDR block`

   ![](/images/5-workshop/2.prerequisite/003-createvpc.png?width=90pc)

   - **Tenancy**: `Default`
   - **Number of Availability Zones**: `2`
   - **Number of public subnets**: `2`
   - **Number of private subnets**: `2`

   ![](/images/5-workshop/2.prerequisite/004-createvpc.png?width=90pc)

   - **NAT gateways**: `None`
   - **VPC endpoints**: `S3 Gateway`
   - **DNS options**: Enable DNS hostnames và Enable DNS resolution

   ![](/images/5-workshop/2.prerequisite/005-createvpc.png?width=90pc)

4. Chọn **Create VPC**

![](/images/5-workshop/2.prerequisite/006-createvpc.png?width=90pc)

5. Sau khi tạo thành công, chọn **View VPC** để xem chi tiết

![](/images/5-workshop/2.prerequisite/007-createvpc.png?width=90pc)

![](/images/5-workshop/2.prerequisite/008-createvpc.png?width=90pc)

{{% notice tip %}}
VPC wizard sẽ tự động tạo Internet Gateway, S3 Gateway Endpoint, Route Tables và associate subnets. NAT Gateway sẽ được tạo thủ công ở bước 5.6.3.
{{% /notice %}}
#### Tạo DynamoDB Endpoint

Vì VPC wizard chỉ tạo S3 Gateway endpoint, chúng ta cần tạo thêm DynamoDB endpoint:

1. Chọn **Endpoints** → **Create endpoint**

![](/images/5-workshop/2.prerequisite/009-createendpoint.png?width=90pc)

2. Cấu hình:
   - **Name**: `carbuyer-dynamodb-endpoint`
   - **Service category**: AWS services

   ![](/images/5-workshop/2.prerequisite/010-createendpoint.png?width=90pc)

   - **Service name**: `com.amazonaws.ap-southeast-1.dynamodb` (Type: **Gateway**)
   - **VPC**: `carbuyer-fcj-vpc`
   - **Route tables**: Chọn 3 route tables (bỏ qua main route table)

   ![](/images/5-workshop/2.prerequisite/011-createendpoint.png?width=90pc)

3. Chọn **Create endpoint**

![](/images/5-workshop/2.prerequisite/012-createendpoint.png?width=90pc)

#### Ghi chú IPv4 CIDR của Public Subnet

Sau khi tạo VPC thành công, hãy ghi lại IPv4 CIDR của Public Subnet AZ 1a:

1. Trong **VPC Console**, chọn **Subnets**

2. Tìm và ghi chú IPv4 CIDR của subnet:
   - **Subnet name**: `carbuyer-fcj-subnet-public1-ap-southeast-1a`
   - **IPv4 CIDR**: `10.0.x.x/20` (ví dụ: 10.0.0.0/20)

![](/images/5-workshop/2.prerequisite/014-subnet-info.png?width=90pc)

{{% notice info %}}
**Quan trọng:** Hãy ghi lại chính xác IPv4 CIDR của **Public Subnet AZ 1a** này. Bạn sẽ cần sử dụng nó để cấu hình Security Group cho Admin Service ở bước 5.6.1.
{{% /notice %}}

Tiếp theo, chúng ta sẽ tạo IAM Role cho EC2 instances.