---
title : "Workshop"
date :  "2024-01-01"
weight : 4
chapter : false
pre : " <b> 4. </b> "
---

# Deploy ứng dụng Node.js lên AWS với kiến trúc Multi-Tier

#### Tổng quan

Chào mừng bạn đến với workshop về Amazon EC2, DynamoDB, S3, CloudFront và AWS Lambda!

Trong workshop này, chúng ta sẽ tìm hiểu và triển khai một ứng dụng Node.js lên AWS sử dụng kiến trúc multi-tier. Chúng ta sẽ khám phá cách thiết lập VPC networking, triển khai EC2 instances, cấu hình DynamoDB database, và triển khai serverless email service với Lambda. Sau đó, chúng ta sẽ áp dụng kiến thức đã học bằng cách triển khai một ứng dụng thương mại điện tử thực tế tên là CarBuyer trên các dịch vụ này.

![](/Internship-report-aws/images/nodejs_x_aws.png)


#### Thời gian

Workshop này có thể mất khoảng **90-120 phút** để hoàn thành.

#### Nội dung

1. **[Giới thiệu](4.1-Introduce/)** - Tìm hiểu về ứng dụng CarBuyer (website bán xe ô tô), kiến trúc tổng quan và các dịch vụ AWS sẽ sử dụng trong workshop bao gồm EC2, DynamoDB, S3, CloudFront, Lambda.

2. **[Các bước chuẩn bị](4.2-Prerequiste/)** - Chuẩn bị hạ tầng mạng và quyền truy cập: tạo VPC với public/private subnets, Internet Gateway, Route Tables, IAM Role cho EC2, IAM User và Access Keys cho ứng dụng.

3. **[Tạo DynamoDB Database](4.3-database/)** - Tạo 12 DynamoDB tables cho các entities như User, XeOto, ThuongHieu, MauXe, KieuDang, NguyenLieuXe, PhuKien, LoaiPhuKien, TinTuc, DanhGia, Slider, DatLichKH. Import dữ liệu mẫu vào các tables.

4. **[Cấu hình S3 và CloudFront](4.4-storage/)** - Tạo S3 bucket để lưu trữ static assets (hình ảnh sản phẩm, tin tức, slider). Cấu hình bucket policy cho public access. Tạo CloudFront distribution để phân phối nội dung với low latency thông qua CDN toàn cầu.

5. **[Lambda Email Service](4.5-setup-email-service/)** - Triển khai serverless email notification service sử dụng AWS Lambda và API Gateway. Cấu hình Lambda function để gửi email xác nhận đặt lịch xem xe, đặt lại mật khẩu. Tạo REST API endpoint và cấu hình API Key security.

6. **[Deploy ứng dụng lên EC2](4.6-deployment/)** - Tạo Security Groups, khởi tạo 2 EC2 instances (Customer Service trong public subnet và Admin/Employee Service trong private subnet). Cấu hình NAT Gateway cho private subnet. Setup Application Load Balancer với path-based routing và sticky sessions. Deploy ứng dụng Node.js với PM2 process manager.

7. **[Dọn dẹp tài nguyên](4.7-cleanup/)** - Xóa tất cả tài nguyên AWS đã tạo theo đúng thứ tự để tránh phát sinh chi phí
