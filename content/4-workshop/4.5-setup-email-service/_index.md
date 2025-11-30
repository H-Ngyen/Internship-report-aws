---
title : "Lambda Email Service"
date :  "2024-01-01" 
weight : 5
chapter : false
pre : " <b> 4.5. </b> "
---

### Lambda Email Service

Trong phần này, chúng ta sẽ triển khai serverless email notification service cho ứng dụng CarBuyer sử dụng AWS Lambda và API Gateway.

#### Giới thiệu về AWS Lambda

AWS Lambda là serverless compute service cho phép bạn chạy code mà không cần quản lý servers. Lambda tự động scale và bạn chỉ trả tiền cho compute time thực tế sử dụng.

**Ưu điểm chính:**

- **Serverless** - Không cần quản lý infrastructure, AWS tự động xử lý scaling và patching
- **Pay-per-use** - Chỉ trả tiền cho số lần invoke và compute time, không có idle costs
- **Auto-scaling** - Tự động scale từ vài requests đến hàng nghìn requests per second
- **Event-driven** - Trigger từ nhiều nguồn như API Gateway, S3, DynamoDB
- **Free tier** - 1 triệu free requests và 400,000 GB-seconds compute time mỗi tháng

#### Giới thiệu về Amazon API Gateway

Amazon API Gateway là fully managed service để tạo, publish, maintain, monitor và secure APIs.

**Ưu điểm chính:**

- **RESTful APIs** - Hỗ trợ REST API với HTTP methods (GET, POST, PUT, DELETE)
- **Security** - API Keys, IAM authorization, Lambda authorizers
- **Throttling** - Rate limiting để bảo vệ backend services
- **Monitoring** - Tích hợp với CloudWatch để theo dõi metrics và logs
- **CORS support** - Dễ dàng cấu hình cross-origin requests

#### Kiến trúc Email Service

Trong workshop này, chúng ta sẽ:

1. **Tạo Lambda function** để:
   - Xử lý email xác nhận đặt lịch xem xe
   - Gửi email đặt lại mật khẩu
   - Sử dụng Gmail SMTP để gửi email

2. **Tạo API Gateway REST API** để:
   - Expose Lambda function qua HTTP endpoint
   - Cấu hình API Key authentication
   - Deploy API lên production stage

3. **Tích hợp với ứng dụng** để:
   - Customer Service và Admin Service gọi API để gửi email
   - Sử dụng API Key để bảo mật requests

{{% notice info %}}
Lambda function sẽ sử dụng Gmail SMTP. Bạn cần có Gmail account và tạo App Password để sử dụng.
{{% /notice %}}

#### Các bước thực hiện

1. [Setup IAM Role & Lambda Function](4.5.1-setup-iam-lambda/)
2. [Test Lambda Function](4.5.2-test-lambda/)
3. [Setup API Gateway](4.5.3-setup-api-gateway/)
4. [Setup API Security](4.5.4-setup-api-security/)

#### Thông tin cần lưu lại

Sau khi hoàn thành các bước, bạn cần lưu lại 2 thông tin quan trọng để sử dụng ở mục 5.6:

**1. API Gateway Invoke URL** (từ bước 4.5.3):
```
https://YOUR_API_ID.execute-api.ap-southeast-1.amazonaws.com/prod
```

**2. API Key** (từ bước 4.5.4):
```
YOUR_GENERATED_API_KEY
```

{{% notice warning %}}
**Lưu ý quan trọng:**
Cả 2 thông tin này sẽ được sử dụng trong file cấu hình `.env` của ứng dụng ở mục 4.6.
{{% /notice %}}
