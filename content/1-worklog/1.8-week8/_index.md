---
title : "Worklog Tuần 8"
date :  "2025-02-24"
weight : 8
chapter : false
pre : " <b> 1.8. </b> "
---

### Mục tiêu tuần 8:
- Bắt đầu giai đoạn triển khai dự án CarBuyer.
- Thiết lập hạ tầng mạng, IAM và cơ sở dữ liệu.
- Bắt đầu viết tài liệu workshop.
- Hoàn thành video và quiz tuần 12 và 13.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
|------|-----------|--------------|-----------------|----------------|
| 2 | - Bắt đầu viết workshop <br> - Triển khai VPC networking <br>&emsp; + Tạo VPC với 2 public + 2 private subnets <br>&emsp; + Cấu hình Internet Gateway và NAT Gateway <br>&emsp; + Thiết lập Route Tables <br> - Thiết lập IAM roles/policies <br>&emsp; + Tạo IAM Role cho EC2 <br>&emsp; + Tạo IAM Role cho Lambda | 03/11/2025 | 03/11/2025 |  |
| 3 | - Tiếp tục viết workshop <br> - Tạo DynamoDB tables <br>&emsp; + Thiết kế schema cho 12 tables <br> - Chuyển đổi mô hình dữ liệu <br>&emsp; + Phân tích schema MongoDB <br>&emsp; + Thiết kế schema DynamoDB | 04/11/2025 | 04/11/2025 |  |
| 4 | - Xem video và làm quiz Tuần 12: Building Data platfrom on AWS (part 1). | 05/11/2025 | 05/11/2025 | |
| 5 | - Xem video và làm quiz Tuần 13: Building Data platfrom on AWS (part 2). | 06/11/2025 | 06/11/2025 | |
| 6 | - Tiếp tục viết workshop <br> - Hoàn thiện website CarBuyer <br>&emsp; + Sửa đổi code để chuyển từ MongoDB sang DynamoDB <br>&emsp; + Test CRUD operations <br>&emsp; + Sửa lỗi và tối ưu code <br> - Tách services ra làm 2 service độc lập (khách hàng và nhân viên/quản trị viên) | 07/11/2025 | 07/11/2025 |  |

### Kết quả đạt được tuần 8:

- Đã triển khai thành công hạ tầng mạng VPC và các vai trò IAM cần thiết.
- Hoàn tất việc tạo 12 bảng DynamoDB và chuyển đổi mô hình dữ liệu từ MongoDB.
- Bắt đầu quá trình viết tài liệu workshop.
- Hoàn thành video và quiz của tuần 12 và 13.

### Khó khăn gặp phải:
- Việc thiết kế schema cho DynamoDB từ một cơ sở dữ liệu quan hệ đòi hỏi sự thay đổi trong tư duy thiết kế.
- Gặp bug trên trang web specialforce.awsstudygroup.com sau khi hoàn thành video của tuần 12 và 13, dẫn đến việc không thể nhận được liên kết chứng chỉ cho các tuần này.

### Kế hoạch tuần sau:
- Hoàn thiện các phần còn lại của tài liệu workshop.
- Triển khai S3 và CloudFront.
- Bắt đầu phát triển Lambda email service.
- Xem video và làm quiz tuần 14.