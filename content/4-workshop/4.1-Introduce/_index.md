---
title : "Giới thiệu"
date :  "2024-01-01" 
weight : 1 
chapter : false
pre : " <b> 4.1. </b> "
---

### Giới thiệu

#### Giới thiệu về Multi-Tier Architecture

- Kiến trúc Multi-Tier là mô hình thiết kế ứng dụng phân tách các thành phần thành nhiều tầng (tiers) độc lập. Mỗi tầng có trách nhiệm riêng biệt và giao tiếp với nhau thông qua các giao diện được định nghĩa rõ ràng.
- Kiến trúc này mang lại nhiều lợi ích như dễ dàng mở rộng và bảo trì, và tách biệt concerns giữa các tầng.

#### Tổng quan về workshop

Trong workshop này, chúng ta sẽ triển khai website thương mại điện tử hoàn chỉnh trên AWS.

- **"Customer Service"** chạy trong public subnet để phục vụ khách hàng truy cập từ internet. Service này xử lý các chức năng như xem danh sách xe, chi tiết sản phẩm, đặt lịch hẹn lái xe.
- **"Admin/Employee Service"** chạy trong private subnet để quản lý nội bộ. Service này chỉ có thể truy cập thông qua Application Load Balancer với path-based routing, xử lý các chức năng quản trị như quản lý sản phẩm, đơn hàng, người dùng và quản lý các mục nhỏ khác.
- **"Lambda Email Service"** là serverless function xử lý việc gửi email thông báo cho khách hàng khi đặt lịch xem xe hoặc khi nhân viên cần đặt lại mật khẩu.

![Architecture Overview](/images/arc-log.png)