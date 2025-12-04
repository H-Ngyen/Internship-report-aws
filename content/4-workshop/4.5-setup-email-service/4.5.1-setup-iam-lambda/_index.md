---
title : "Setup IAM Role & Lambda Function"
date :  "2024-01-01" 
weight : 1
chapter : false
pre : " <b> 4.5.1. </b> "
---

### Setup IAM Role & Lambda Function

Trong phần này, chúng ta sẽ tạo IAM Role và Lambda function để xử lý việc gửi email.

#### 1. Tạo IAM Role cho Lambda trên Console

Truy cập [IAM Console](https://console.aws.amazon.com/iam/) → **Roles** → **Create role**:

![](/Internship-report-aws/images/5-workshop/2.prerequisite/014-createrole.png?width=90pc)

#### 2. Chọn trusted entity

Chọn:
- **Trusted entity type**: `AWS service`
- **Use case**: `Lambda`

![](/Internship-report-aws/images/5-workshop/5.email/007-trusted-entity.png?width=90pc)

#### 3. Gán permissions

Tìm và chọn policy: `AWSLambdaBasicExecutionRole`

![](/Internship-report-aws/images/5-workshop/5.email/008-permissions.png?width=90pc)

#### 4. Đặt tên role

- **Role name**: `carbuyer-lambda-email-role`
- **Description**: `Role for Lambda email service`

Click **Create role**

![](/Internship-report-aws/images/5-workshop/5.email/009-role-name.png?width=90pc)

#### 5. Tạo Lambda function trên Console

Truy cập [Lambda Console](https://console.aws.amazon.com/lambda/) → **Create a function**:

![](/Internship-report-aws/images/5-workshop/5.email/005-create-function.png?width=90pc)

**Chọn tùy chọn tạo function:**
- Chọn **Author from scratch**

**Basic information:**
- **Function name**: `carbuyer-email-service`
- **Runtime**: Node.js 22.x
- **Architecture**: x86_64

![](/Internship-report-aws/images/5-workshop/5.email/006-create-function.png?width=90pc)

**Permissions:**
- Click **Change default execution role**
- Chọn **Use an existing role**
- **Existing role**: `carbuyer-lambda-email-role`

Click **Create function**

![](/Internship-report-aws/images/5-workshop/5.email/007-create-function.png?width=90pc)

#### 6. Tải và upload deployment package

Tải file zip từ GitHub:
- [Tải lambda-email-service.zip](https://github.com/khaizr0/RAB_Data/raw/refs/heads/main/lambda-email-service.zip)

Trong tab **Code** → **Upload from** → **.zip file**:
- Chọn file `lambda-email-service.zip` vừa tải
- Click **Save**

![](/Internship-report-aws/images/5-workshop/5.email/006-upload-code.png?width=90pc)

#### 7. Cấu hình Environment Variables

Trong tab **Configuration** → **Environment variables** → **Edit**:

![](/Internship-report-aws/images/5-workshop/5.email/007-env-variables.png?width=90pc)

{{% notice info %}}
Bạn có thể sử dụng Gmail SMTP hoặc Amazon SES. Trong workshop này sẽ sử dụng Gmail SMTP
{{% /notice %}}
Thêm các biến môi trường:
- `EMAIL_HOST`: `smtp.gmail.com`
- `EMAIL_PORT`: `465`
- `EMAIL_USER`: `your-email@gmail.com` (thay bằng email thật)
- `EMAIL_PASS`: `your-16-char-app-password` (App Password của bạn)

Click **Save**

![](/Internship-report-aws/images/5-workshop/5.email/008-env-variables.png?width=90pc)

#### 8. Cấu hình General settings

Trong tab **Configuration** → **General configuration** → **Edit**:

![](/Internship-report-aws/images/5-workshop/5.email/008-1-env-variables.png?width=90pc)

- **Timeout**: 30 seconds
- **Memory**: 256 MB

Click **Save**

![](/Internship-report-aws/images/5-workshop/5.email/008-general-config.png?width=90pc)

Bạn đã hoàn thành việc setup IAM Role và Lambda function! Tiếp theo chuyển sang [4.5.2 - Test Lambda Function](../4.5.2-test-lambda).