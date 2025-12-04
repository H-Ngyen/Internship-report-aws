---
title : "Bản đề xuất"
date :  "2025-11-24"
weight : 2
chapter : false
pre : " <b> 2. </b> "
---

## Triển khai trang web thương mại điện tử mua bán xe ô tô lên AWS với kiến trúc Multi-Tier

### 1. Tóm tắt dự án

**CarBuyer** là trang web thương mại điện tử chuyên mua bán xe ô tô được xây dựng hoàn toàn trên AWS Cloud với kiến trúc **Multi-Tier**. Trang web cung cấp trải nghiệm mua sắm trực tuyến cho khách hàng và hệ thống quản lý nội bộ cho nhân viên và quản trị viên.

**Khách hàng** có thể dễ dàng tìm kiếm và xem chi tiết các mẫu xe, đặt lịch lái thử, và nhận email xác nhận tự động ngay sau khi đăng ký. **Nhân viên** được trang bị công cụ quản lý toàn diện cho sản phẩm (xe và phụ kiện), lịch hẹn, cùng với khả năng cập nhật nội dung website như tin tức và banner quảng cáo. **Quản trị viên** có quyền cao nhất để quản lý thông tin và tài khoản của toàn bộ nhân viên trong hệ thống.

Hệ thống được thiết kế với kiến trúc **Multi-Tier** trên AWS, tận dụng các dịch vụ managed services để đảm bảo khả năng mở rộng linh hoạt, bảo mật cao và chi phí tối ưu:

- **Amazon EC2** — Chạy 2 web services Node.js độc lập: Customer Service (public subnet) và Admin/Employee Service (private subnet)
- **Amazon VPC** — Cách ly mạng với 2 public subnets và 2 private subnets trên 2 Availability Zones
- **Amazon DynamoDB** — Cơ sở dữ liệu NoSQL serverless với 12 tables, tự động scale theo nhu cầu
- **Amazon S3 + CloudFront** — Lưu trữ hình ảnh sản phẩm và phân phối nhanh chóng qua mạng CDN toàn cầu
- **AWS Lambda + API Gateway** — Xử lý gửi email thông báo (xác nhận đặt lịch, reset mật khẩu) theo mô hình serverless
- **Application Load Balancer** — Phân phối traffic thông minh với path-based routing và health checks

---

### 2. Vấn đề và giải pháp

#### Vấn đề hiện tại

Trang web CarBuyer ban đầu được phát triển với MongoDB và lưu trữ file dữ liệu và ảnh local nên gặp các vấn đề như sau:

- Khó khăn trong việc scale và backup database
- Không có CDN để phân phối hình ảnh nhanh chóng
- Thiếu hệ thống email notification tự động
- Quản lý infrastructure và database tốn khá nhiều công sức

#### Giải pháp đề xuất

Để giải quyết các vấn đề trên, **CarBuyer** được migrate lên AWS Cloud với kiến trúc **Multi-Tier**, tận dụng tối đa các **Managed Services** để giảm tải vận hành và tăng hiệu suất:

- **DynamoDB** thay MongoDB — Serverless database, auto-scaling
- **S3 + CloudFront** — Lưu trữ và phân phối hình ảnh qua CDN, giảm latency 60-70%
- **Lambda + API Gateway** — Gửi email tự động (xác nhận đặt lịch, reset password)
- **VPC** — Cách ly mạng với public/private subnets
- **Application Load Balancer** — Phân phối traffic với path-based routing
- **EC2** — Chạy Node.js/Express.js với PM2 manager

---

### Lợi ích & Hiệu quả đầu tư

- **Giảm chi phí vận hành** — Tiết kiệm 35-40% so với VPS truyền thống nhờ managed services
- **Giảm 80% thời gian vận hành** — Không cần quản lý server, database, backup
- **Cải thiện performance** — CloudFront CDN giảm latency lên tới 60-70%
- **High availability** — Hệ thống 24/7 với Multi-AZ deployment
- **Tự động mở rộng** — DynamoDB auto-scaling, Lambda serverless
- **Email tự động** — Lambda gửi email xác nhận đặt lịch, đặt lại mật khẩu

**Chi phí hàng tháng ước tính (không tính Free Tier): ≈ $85.54 USD**  
**Chi phí hàng năm: ≈ $1,026 USD**

### 3. Kiến trúc hệ thống

Hệ thống được thiết kế theo mô hình **Multi-Tier Architecture** với 3 tầng độc lập, giúp dễ dàng quản lý, bảo trì và mở rộng:

#### **Application Tier (Tầng Ứng dụng)**
- **Node.js/Express.js**: Server-Side Rendering (SSR) xử lý business logic và render HTML động trên server
- **Customer Service** (Public Subnet): Web service cho khách hàng, truy cập từ internet
- **Admin/Employee Service** (Private Subnet): Web service quản lý nội bộ, bảo vệ bởi private subnet
- **Application Load Balancer**: Phân phối traffic giữa 2 services với path-based routing
- **PM2 Process Manager**: Quản lý và giám sát tiến trình Node.js
- **JWT + Express-session**: Xác thực và quản lý phiên

#### **Data Tier (Tầng Dữ liệu)**
- **Amazon DynamoDB**: 12 tables NoSQL lưu trữ dữ liệu (User, XeOto, ThuongHieu, MauXe, KieuDang, NguyenLieuXe, PhuKien, LoaiPhuKien, TinTuc, DanhGia, Slider, DatLichKH)
- **Amazon S3**: Lưu trữ hình ảnh sản phẩm, tin tức, slider
- **Amazon CloudFront**: CDN phân phối hình ảnh nhanh chóng

#### **Integration Tier (Tầng Tích hợp)**
- **AWS Lambda**: Serverless function xử lý gửi email (xác nhận đặt lịch, reset mật khẩu)
- **Amazon API Gateway**: REST API endpoints với API Key authentication

![Architecture Overview](/Internship-report-aws/images/arc-log.png)

---

### Dịch vụ AWS được sử dụng

| Danh mục | Dịch vụ |
|----------|--------|
| **Compute & Networking** | EC2 (2 × t3.micro instances), VPC (2 public + 2 private subnets), Internet Gateway, NAT Gateway, Application Load Balancer |
| **Database & Storage** | DynamoDB (12 tables), S3 (object storage), CloudFront (CDN) |
| **Serverless & Integration** | Lambda (email service), API Gateway (REST API) |
| **Security & Access** | IAM (roles & policies), Security Groups, VPC Gateway Endpoints (S3, DynamoDB) |

---

### 4. Triển khai kỹ thuật

#### Các giai đoạn triển khai

Dự án migration CarBuyer lên AWS trải qua 4 giai đoạn chính:

1. **Nghiên cứu và thiết kế kiến trúc**: Nghiên cứu AWS services (VPC, EC2, DynamoDB, S3, Lambda, ALB) và thiết kế kiến trúc Multi-Tier phù hợp với yêu cầu bảo mật và khả năng mở rộng. Vẽ sơ đồ kiến trúc và xác định các components cần thiết.

2. **Tính toán chi phí và kiểm tra tính khả thi**: Sử dụng AWS Pricing Calculator để ước tính chi phí các dịch vụ (EC2, ALB, NAT Gateway, DynamoDB, S3, CloudFront, Lambda), đảm bảo phù hợp ngân sách và hiệu quả đầu tư. Đánh giá tính khả thi của giải pháp.

3. **Điều chỉnh kiến trúc để tối ưu chi phí/giải pháp**: Tinh chỉnh kiến trúc (ví dụ: sử dụng VPC Gateway Endpoints cho S3/DynamoDB để giảm chi phí NAT Gateway, chọn DynamoDB on-demand thay vì provisioned) để cân bằng giữa hiệu suất và chi phí.

4. **Phát triển, kiểm thử, triển khai**: Xây dựng VPC networking, migrate database từ MongoDB sang DynamoDB, phát triển Lambda email service, deploy Node.js applications lên EC2 với PM2, cấu hình ALB và CloudFront, sau đó kiểm thử end-to-end và đưa vào vận hành.

#### Yêu cầu kỹ thuật

**Application Layer**: Node.js/Express.js với SSR, PM2 process manager quản lý 2 services (Customer và Admin/Employee). Sử dụng JWT + express-session cho authentication. Frontend HTML/CSS/JavaScript render động từ server.

**AWS Infrastructure**: Kiến trúc Multi-Tier với VPC (2 public + 2 private subnets trên 2 AZs), EC2 t3.micro instances, Application Load Balancer (path-based routing), NAT Gateway, Internet Gateway, Security Groups, IAM roles/policies.

**Data & Storage**: DynamoDB (12 tables NoSQL: User, XeOto, ThuongHieu, MauXe, KieuDang, NguyenLieuXe, PhuKien, LoaiPhuKien, TinTuc, DanhGia, Slider, DatLichKH), S3 (lưu trữ hình ảnh), CloudFront CDN (phân phối nội dung), VPC Gateway Endpoints (S3, DynamoDB).

**Serverless Integration**: Lambda function (Nodemailer + Gmail SMTP) xử lý email notifications (xác nhận đặt lịch, reset password), API Gateway với REST endpoints và API Key authentication.

**Development Tools**: AWS SDK (@aws-sdk/client-dynamodb, @aws-sdk/client-s3, @aws-sdk/lib-dynamodb), AWS CLI, Git, SSH, Nodemailer.

---

### 5. Lộ trình & Mốc hoàn thành

| Tháng | Kết quả |
|-------|--------|
| **Tháng 1** | Hoàn thành học AWS fundamentals, thiết kế kiến trúc. Hoàn thiện VPC networking, IAM setup, DynamoDB tables, S3 + CloudFront |
| **Tháng 2** | Hoàn thiện SSR application (Node.js), Lambda email service, API Gateway, EC2 deployment, ALB configuration |
| **Tháng 3** | Testing, optimization, workshop documentation |
| **Cuối tháng 3** | Triển khai bản Production |

---

### 6. Ước tính chi phí

#### Chi phí dịch vụ AWS (ước tính cho 1,000 - 1,500 người dùng hoạt động/tháng, không tính Free Tier)

| Dịch vụ | Mô tả | Chi phí tháng (USD) |
|---------|-------|--------------------|
| **EC2** | 2 × t3.micro instances (730 hours) | **$20.44** |
| **Application Load Balancer** | 730 hours + LCU charges | **$21.32** |
| **NAT Gateway** | 730 hours + data processing (2GB) | **$43.10** |
| **DynamoDB** | 12 tables, on-demand mode, 1GB storage | **$0.29** |
| **S3 Standard** | 10GB storage + 25K requests | **$0.28** |
| **CloudFront** | CDN distribution, 5GB origin transfer | **$0.10** |
| **Lambda** | Email service (1K requests/month) | **$0.01** |
| **API Gateway** | REST API (1K requests/month) | **$0.00** |

**➡ Tổng chi phí hàng tháng:** ≈ **$85.54 USD**  
**➡ Chi phí hàng năm:** ≈ **$1,026 USD**

---

### 7. Đánh giá rủi ro

#### Ma trận rủi ro

| Rủi ro | Mức độ ảnh hưởng | Xác suất |
|--------|------------------|----------|
| Chi phí vượt ngân sách | Trung bình | Thấp |
| Security vulnerabilities | Cao | Trung bình |
| Performance issues | Trung bình | Thấp |
| Email delivery failures | Thấp | Trung bình |

**Giải pháp giảm thiểu:**

- Thiết lập cảnh báo chi phí CloudWatch và AWS Budgets
- Áp dụng nguyên tắc **least privilege** cho IAM roles (chỉ cấp quyền tối thiểu cần thiết)
- Sử dụng Security Groups restrictive rules và private subnets
- Implement retry logic và error logging trong Lambda
- CloudFront CDN và DynamoDB auto-scaling cho performance

---

### 8. Kết quả kỳ vọng

#### Kết quả kỹ thuật

- Hoàn thiện nền tảng thương mại điện tử bán xe ô tô với kiến trúc Multi-Tier.
- Hệ thống bảo mật và mở rộng tốt với VPC, Security Groups, ALB, CloudFront.
- Email notifications tự động với Lambda và API Gateway.
- Giảm 80% thời gian vận hành và tiết kiệm 35-40% chi phí so với VPS truyền thống.

#### Giá trị lâu dài

- Thể hiện năng lực thực hành về Serverless, DevOps.
- Có thể mở rộng lên hàng nghìn người dùng mà không cần thay đổi kiến trúc.
- Là mẫu kiến trúc chuẩn AWS có thể tái sử dụng cho các dự án sau.
