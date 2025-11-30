--- 
title : "Worklog Tuần 9"
date :  "2024-01-01"
weight : 9
chapter : false
pre : " <b> 1.9. </b> "
---

### Mục tiêu tuần 9:
- Hoàn thiện các phần còn lại của tài liệu workshop.
- Triển khai S3, CloudFront và Lambda email service.
- Bắt đầu triển khai ứng dụng lên EC2 và cấu hình cân bằng tải.
- Hoàn thành video và quiz tuần 14.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
|------|-----------|--------------|-----------------|----------------|
| 2 | - Tiếp tục viết workshop <br> - Thiết lập S3 và CloudFront <br>&emsp; + Tạo S3 bucket cho hình ảnh <br>&emsp; + Cấu hình bucket policies <br>&emsp; + Tạo CloudFront distribution <br>&emsp; + Cấu hình VPC Gateway Endpoint cho S3 <br> - Phát triển Lambda email service <br>&emsp; + Tạo Lambda function với Nodemailer <br>&emsp; + Cấu hình SMTP <br>&emsp; + Tạo API Gateway với REST endpoints | 10/11/2025 | 10/11/2025 |  |
| 3 | - Xem video và làm quiz Tuần 14: Introduction to Machine Learning. | 11/11/2025 | 11/11/2025 | <https://specialforce.awsstudygroup.com/#/cert/week-14:-introduction-to-machine-learning> |
| 4 | - Tiếp tục viết workshop <br> - Deploy ứng dụng lên EC2 <br>&emsp; + Tạo Security Groups <br>&emsp; + Khởi tạo EC2 instances <br>&emsp; + Cài đặt Node.js và PM2 <br>&emsp; + Deploy Customer và Admin services <br> - Cấu hình Application Load Balancer <br>&emsp; + Tạo Target Groups <br>&emsp; + Thiết lập path-based routing <br> - Sửa đổi một số lỗi của ứng dụng sau khi deploy | 12/11/2025 | 12/11/2025 |  |
| 5 | - Tiếp tục hoàn thiện workshop | 13/11/2025 | 13/11/2025 |  |
| 6 | - Tiếp tục hoàn thiện workshop | 14/11/2025 | 14/11/2025 |  |

### Kết quả đạt được tuần 9:

- Đã hoàn thành các phần còn lại của tài liệu workshop, bao gồm triển khai S3, CloudFront và phát triển dịch vụ email Lambda.
- Ứng dụng đã được triển khai lên EC2 với cấu hình cân bằng tải ALB.
- Hoàn thành video và quiz của tuần 14.

### Khó khăn gặp phải:
- Việc cấu hình chính xác path-based routing trên ALB để định tuyến giữa các dịch vụ khách hàng và quản trị viên đòi hỏi nhiều thử nghiệm.
- Gặp phải một số lỗi không mong muốn sau khi triển khai ứng dụng, cần thời gian để gỡ lỗi và sửa chữa.

### Kế hoạch tuần sau:
- Kiểm thử toàn diện hệ thống (Customer, Admin, Lambda email).
- Sửa lỗi và tối ưu hóa hiệu suất, cải thiện UI/UX.
- Tiếp tục hoàn thiện tài liệu workshop.
- Xem video và làm quiz tuần 15.
