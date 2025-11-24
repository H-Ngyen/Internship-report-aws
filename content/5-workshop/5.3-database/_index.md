---
title : "Tạo DynamoDB Database"
date :  "2024-01-01" 
weight : 3
chapter : false
pre : " <b> 5.3. </b> "
---

### Tạo DynamoDB Database

Trong phần này, chúng ta sẽ tạo các DynamoDB tables cần thiết cho ứng dụng CarBuyer và import dữ liệu mẫu.

#### Giới thiệu về Amazon DynamoDB

Amazon DynamoDB là dịch vụ cơ sở dữ liệu NoSQL được quản lý hoàn toàn (fully managed), cung cấp hiệu suất nhanh và có thể dự đoán với khả năng mở rộng liền mạch.

**Ưu điểm chính:**

- **Hiệu suất cao** - Độ trễ thấp ở mức single-digit milliseconds cho cả read và write operations
- **Serverless** - Không cần quản lý server, tự động scale theo nhu cầu
- **Flexible billing** - On-demand pricing mode chỉ trả tiền khi sử dụng, không có minimum capacity
- **High availability** - Tự động replicate data across multiple Availability Zones
- **Tích hợp tốt** - Native integration với các AWS services khác như Lambda, API Gateway, S3

#### Cấu trúc Database

Ứng dụng CarBuyer sử dụng 12 DynamoDB tables để lưu trữ dữ liệu:

| Table | Mô tả | Partition Key |
|-------|-------|---------------|
| User | Thông tin người dùng (admin, employee, customer) | id (String) |
| XeOto | Thông tin xe ô tô (model, giá, specs) | id (String) |
| ThuongHieu | Thương hiệu xe và phụ kiện | id (String) |
| MauXe | Màu sắc xe | id (String) |
| KieuDang | Kiểu dáng xe (Sedan, SUV, Hatchback...) | id (String) |
| NguyenLieuXe | Loại nhiên liệu (Xăng, Dầu, Hybrid, Electric) | id (String) |
| PhuKien | Thông tin phụ kiện xe | id (String) |
| LoaiPhuKien | Loại phụ kiện (nội thất, ngoại thất...) | id (String) |
| TinTuc | Tin tức và bài viết | id (String) |
| DanhGia | Đánh giá của khách hàng | id (String) |
| Slider | Ảnh slider trang chủ | id (String) |
| DatLichKH | Lịch hẹn lái thử xe của khách hàng | id (String) |

![DynamoDB Architecture](/images/arc-database.png)

#### Nội dung

1. [Tạo DynamoDB Tables](5.3.1-create-tables/)
2. [Import dữ liệu mẫu](5.3.2-import-data/)
