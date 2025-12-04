---
title : "Setup API Security"
date :  "2024-01-01" 
weight : 4
chapter : false
pre : " <b> 4.5.4. </b> "
---

### Setup API Security

In this section, we will create an API Key and Usage Plan to secure the API Gateway.

#### 1. Create API Key for Security

In API Gateway Console → **API Keys** → **Create API Key**:

![](/Internship-report-aws/images/5-workshop/5.email/018-api-gateway-rest.png?width=90pc)

**API key details:**
- **Name**: `carbuyer-email-api-key`
- **Description**: `API key for CarBuyer email service` (optional)

**API key:**
- Select **Auto generate**

Click **Save**

![](/Internship-report-aws/images/5-workshop/5.email/020-api-gateway-rest.png?width=90pc)

Save the **API Key** for later use

![](/Internship-report-aws/images/5-workshop/5.email/021-api-gateway-rest.png?width=90pc)

#### 2. Create Usage Plan

Click **Usage Plans** → **Create**:

![](/Internship-report-aws/images/5-workshop/5.email/022-api-gateway-rest.png?width=90pc)

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

![](/Internship-report-aws/images/5-workshop/5.email/023-usage-plan.png?width=90pc)

#### 3. Add API Stage to Usage Plan

Go back to **Usage Plans** → click on `carbuyer-email-plan`:

![](/Internship-report-aws/images/5-workshop/5.email/024-usage-plan.png?width=90pc)

**In Associated stages tab:**
- Click **Add API Stage**

![](/Internship-report-aws/images/5-workshop/5.email/025-usage-plan.png?width=90pc)

- **API**: Select `carbuyer-email-api`
- **Stage**: Select `prod`
- Click **Add to usage plan**

![](/Internship-report-aws/images/5-workshop/5.email/033-usage-plan.png?width=90pc)

#### 4. Add API Key to Usage Plan

**In Associated API keys tab:**
- Click **Add API Key**

![](/Internship-report-aws/images/5-workshop/5.email/034-api-key.png?width=90pc)

- Select `carbuyer-email-api-key`
- Click **Add API Key**

![](/Internship-report-aws/images/5-workshop/5.email/035-api-key.png?width=90pc)

{{% notice warning %}}
**Save the API Key:**
Copy this API Key for use in section 4.6 Deploy EC2
{{% /notice %}}

Now proceed to [4.6 - Deployment](../../4.6-deployment) to deploy the application to EC2.