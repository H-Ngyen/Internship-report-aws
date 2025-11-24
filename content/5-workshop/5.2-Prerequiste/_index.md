---
title : "Các bước chuẩn bị"
date :  "2024-01-01" 
weight : 2 
chapter : false
pre : " <b> 5.2. </b> "
---

### Các bước chuẩn bị

Trong phần này, chúng ta sẽ chuẩn bị hạ tầng mạng và quyền truy cập cần thiết để triển khai ứng dụng CarBuyer lên AWS.

#### Yêu cầu

Trước khi bắt đầu workshop, bạn cần có:

- **Tài khoản AWS** - Có thể sử dụng Free Tier cho hầu hết các dịch vụ
- **Kiến thức cơ bản** - Hiểu biết về Node.js, networking và các khái niệm AWS cơ bản
- **Trình duyệt web** - Để truy cập AWS Console

#### Tổng quan

Chúng ta sẽ thiết lập các tài nguyên nền tảng sau:

- **Amazon VPC** với 4 subnets (2 public, 2 private) trên 2 Availability Zones để đảm bảo high availability
- **Internet Gateway** để cho phép traffic từ internet vào public subnets
- **Route Tables** để điều hướng traffic giữa các subnets
- **VPC Endpoints** (S3 Gateway và DynamoDB Gateway) để truy cập AWS services mà không cần phải chạy ra ngoài internet
- **IAM Role** cho EC2 instances để truy cập DynamoDB và S3
- **IAM User và Access Keys** cho ứng dụng Node.js sử dụng AWS SDK

{{% notice info %}}
NAT Gateway sẽ được tạo sau ở bước 5.6.3 khi cần thiết cho private subnet.
{{% /notice %}}

#### Nội dung

1. [Tạo VPC và Network](5.2.1-create-vpc/)
2. [Tạo IAM Role cho EC2](5.2.2-create-iam-role/)
3. [Tạo IAM User và Access Keys](5.2.3-create-access-keys/)
