---
title : "Triển khai ứng dụng lên EC2"
date :  "2024-01-01" 
weight : 6
chapter : false
pre : " <b> 5.6. </b> "
---

### Triển khai ứng dụng lên EC2

Trong phần này, chúng ta sẽ triển khai ứng dụng CarBuyer lên Amazon EC2 instances với 2 services riêng biệt.

#### Giới thiệu về Amazon EC2

Amazon EC2 (Elastic Compute Cloud) cung cấp virtual servers có thể scale trong cloud, cho phép bạn chạy ứng dụng với cấu hình linh hoạt.

**Ưu điểm chính:**

- **Flexible** - Nhiều instance types với cấu hình CPU, memory, storage khác nhau
- **Scalable** - Dễ dàng scale up/down theo nhu cầu
- **Cost-effective** - Chỉ trả tiền cho compute capacity thực tế sử dụng
- **Secure** - Security Groups và Network ACLs để kiểm soát traffic
- **Reliable** - Deploy trên multiple Availability Zones để đảm bảo high availability

#### Giới thiệu về Application Load Balancer

Application Load Balancer (ALB) hoạt động ở layer 7 (application layer), phân phối incoming traffic đến multiple targets như EC2 instances.

**Ưu điểm chính:**

- **Path-based routing** - Route requests dựa trên URL path
- **Health checks** - Tự động kiểm tra health của targets và chỉ route đến healthy instances
- **SSL/TLS termination** - Xử lý HTTPS connections
- **High availability** - Tự động distribute traffic across multiple Availability Zones
- **Integration** - Tích hợp tốt với Auto Scaling, CloudWatch, và các AWS services khác

#### Kiến trúc Deployment

Trong workshop này, chúng ta sẽ triển khai 2 ứng dụng Node.js riêng biệt:

1. **Customer Service** (Public subnet):
   - EC2 instance chạy Node.js application
   - Phục vụ khách hàng: xem xe, đặt lịch lái thử, mua phụ kiện
   - Truy cập từ internet qua Application Load Balancer
   - Kết nối với DynamoDB qua VPC Gateway Endpoint

2. **Admin/Employee Service** (Private subnet):
   - EC2 instance chạy Node.js application
   - Quản lý nội bộ: CRUD xe, phụ kiện, tin tức, đơn hàng, khách hàng
   - Truy cập qua ALB (cho admin) hoặc SSH (cho employee)
   - Kết nối internet qua NAT Gateway để download packages
   - Kết nối với DynamoDB qua VPC Gateway Endpoint

3. **Application Load Balancer**:
   - Phân phối traffic đến cả 2 EC2 instances
   - Health checks để đảm bảo availability
   - Path-based routing: `/` → Customer Service, `/admin` → Admin Service

4. **NAT Gateway**:
   - Cho phép Admin Service (private subnet) truy cập internet
   - Cần thiết để download npm packages và system updates

5. **VPC Gateway Endpoints**:
   - DynamoDB endpoint: Truy cập DynamoDB mà không qua internet
   - S3 endpoint: Upload/download media files từ S3

#### Nội dung

1. [Tạo Security Groups](5.6.1-create-security-groups/)
2. [Tạo EC2 Instances](5.6.2-create-ec2/)
3. [Cấu hình Network](5.6.3-network-config/)
4. [Setup Application Load Balancer](5.6.4-setup-alb/)
5. [Deploy Applications](5.6.5-deploy-apps/)
6. [Test Application](5.6.6-test-application/)