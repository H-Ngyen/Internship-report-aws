---
title : "Setup API Gateway"
date :  "2024-01-01" 
weight : 3
chapter : false
pre : " <b> 4.5.3. </b> "
---

### Setup API Gateway

Trong phần này, chúng ta sẽ tạo REST API và deploy để có thể gọi Lambda function từ bên ngoài.

#### 1. Tạo API Gateway REST API

Truy cập [API Gateway Console](https://console.aws.amazon.com/apigateway/) → **Create API**:

![](/Internship-report-aws/images/5-workshop/5.email/015-api-gateway-rest.png?width=90pc)

- Chọn **REST API** → **Build**

![](/Internship-report-aws/images/5-workshop/5.email/016-api-gateway-rest.png?width=90pc)

- **API name**: `carbuyer-email-api`
- **Description**: `API for Lambda email service`
- **Endpoint Type**: Regional
- **IP address type**: IPv4

Click **Create API**

![](/Internship-report-aws/images/5-workshop/5.email/017-api-gateway-rest.png?width=90pc)

![](/Internship-report-aws/images/5-workshop/5.email/019-api-gateway-rest.png?width=90pc)

#### 2. Tạo Method

Trong API vừa tạo:

**Tạo Method trên root resource:**
- Chọn resource `/`
- Click **Create method**

![](/Internship-report-aws/images/5-workshop/5.email/026-create-method.png?width=90pc)

**Method details:**
- **Method type**: `POST`
- **Integration type**: `Lambda function`
- **Lambda proxy integration**: ✅

![](/Internship-report-aws/images/5-workshop/5.email/027-create-method.png?width=90pc)

- **Lambda function**: `arn:aws:lambda:ap-southeast-1:442228338540:function:carbuyer-email-service`
- **Integration timeout**: `29000`

**Method request settings:**
- **Authorization**: `None`
- **Request validator**: `None`
- **API key required**: ✅

![](/Internship-report-aws/images/5-workshop/5.email/028-create-method.png?width=90pc)

Click **Create method** và kiểm tra kết quả

![](/Internship-report-aws/images/5-workshop/5.email/029-create-method.png?width=90pc)

#### 3. Deploy API

Sau khi tạo method thành công, tìm nút **Deploy API** ở góc trên bên phải:

![](/Internship-report-aws/images/5-workshop/5.email/030-deploy-api.png?width=90pc)

Click **Deploy API**:
- **Deployment stage**: `*New stage*`
- **Stage name**: `prod`
- **Stage description**: `Production stage`

![](/Internship-report-aws/images/5-workshop/5.email/031-deploy-api.png?width=90pc)

Click **Deploy**

Lưu lại **Invoke URL** để sử dụng trong EC2

![](/Internship-report-aws/images/5-workshop/5.email/032-deploy-api.png?width=90pc)

{{% notice warning %}}
**Lưu lại Invoke URL:**
Sao chép URL này để sử dụng trong mục 5.6 Deploy EC2
{{% /notice %}}

Bạn đã hoàn thành việc setup API Gateway! Tiếp theo chuyển sang [4.5.4 - Setup API Security](../4.5.4-setup-api-security).