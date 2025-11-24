---
title : "Setup API Security"
date :  "2024-01-01" 
weight : 4
chapter : false
pre : " <b> 5.5.4. </b> "
---

### Setup API Security

Trong phần này, chúng ta sẽ tạo API Key và Usage Plan để bảo mật API Gateway.

#### 16. Tạo API Key cho bảo mật

Trong API Gateway Console → **API Keys** → **Create API Key**:

![](/images/5-workshop/5.email/018-api-gateway-rest.png?width=90pc)

**API key details:**
- **Name**: `carbuyer-email-api-key`
- **Description**: `API key for CarBuyer email service` (optional)

**API key:**
- Chọn **Auto generate**

Click **Save**

![](/images/5-workshop/5.email/020-api-gateway-rest.png?width=90pc)

Lưu lại **API Key** để sử dụng sau này

![](/images/5-workshop/5.email/021-api-gateway-rest.png?width=90pc)

#### 17. Tạo Usage Plan

Click **Usage Plans** → **Create**:

![](/images/5-workshop/5.email/022-api-gateway-rest.png?width=90pc)

**Usage plan details:**
- **Name**: `carbuyer-email-plan`
- **Description**: `Usage plan for CarBuyer email API` (optional)

**Throttling:**
- **Rate**: `100` requests per second
- **Burst**: `200` requests

**Quota:**
- **Requests**: `10000`
- **Per**: `month`

Click **Create usage plan**

![](/images/5-workshop/5.email/023-usage-plan.png?width=90pc)

#### 18. Thêm API Stage vào Usage Plan

Quay lại **Usage Plans** → click vào `carbuyer-email-plan`:

![](/images/5-workshop/5.email/024-usage-plan.png?width=90pc)

**Trong tab Associated stages:**
- Click **Add API Stage**

![](/images/5-workshop/5.email/025-usage-plan.png?width=90pc)

- **API**: Chọn `carbuyer-email-api`
- **Stage**: Chọn `prod`
- Click **Add to usage plan**

![](/images/5-workshop/5.email/033-usage-plan.png?width=90pc)

#### 19. Thêm API Key vào Usage Plan

**Trong tab Associated API keys:**
- Click **Add API Key**

![](/images/5-workshop/5.email/034-api-key.png?width=90pc)

- Chọn `carbuyer-email-api-key`
- Click **Add API Key**

![](/images/5-workshop/5.email/035-api-key.png?width=90pc)

{{% notice warning %}}
**Lưu lại API Key:**
Sao chép API Key này để sử dụng trong mục 5.6 Deploy EC2
{{% /notice %}}

Tiếp theo chuyển sang [5.6 - Deployment](../../5.6-deployment) để deploy ứng dụng lên EC2.