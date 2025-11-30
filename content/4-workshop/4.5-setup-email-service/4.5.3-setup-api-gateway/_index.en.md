---
title : "Setup API Gateway"
date :  "2024-01-01" 
weight : 3
chapter : false
pre : " <b> 4.5.3. </b> "
---

### Setup API Gateway

In this section, we will create a REST API and deploy it to call the Lambda function from outside.

#### 1. Create API Gateway REST API

Access [API Gateway Console](https://console.aws.amazon.com/apigateway/) → **Create API**:

![](/images/5-workshop/5.email/015-api-gateway-rest.png?width=90pc)

- Select **REST API** → **Build**

![](/images/5-workshop/5.email/016-api-gateway-rest.png?width=90pc)

- **API name**: `carbuyer-email-api`
- **Description**: `API for Lambda email service`
- **Endpoint Type**: Regional
- **IP address type**: IPv4

Click **Create API**

![](/images/5-workshop/5.email/017-api-gateway-rest.png?width=90pc)

![](/images/5-workshop/5.email/019-api-gateway-rest.png?width=90pc)

#### 2. Create Method

In the newly created API:

**Create Method on root resource:**
- Select resource `/`
- Click **Create method**

![](/images/5-workshop/5.email/026-create-method.png?width=90pc)

**Method details:**
- **Method type**: `POST`
- **Integration type**: `Lambda function`
- **Lambda proxy integration**: ✅

![](/images/5-workshop/5.email/027-create-method.png?width=90pc)

- **Lambda function**: `arn:aws:lambda:ap-southeast-1:442228338540:function:carbuyer-email-service`
- **Integration timeout**: `29000`

**Method request settings:**
- **Authorization**: `None`
- **Request validator**: `None`
- **API key required**: ✅

![](/images/5-workshop/5.email/028-create-method.png?width=90pc)

Click **Create method** and verify the result

![](/images/5-workshop/5.email/029-create-method.png?width=90pc)

#### 3. Deploy API

After successfully creating the method, find the **Deploy API** button in the top right corner:

![](/images/5-workshop/5.email/030-deploy-api.png?width=90pc)

Click **Deploy API**:
- **Deployment stage**: `*New stage*`
- **Stage name**: `prod`
- **Stage description**: `Production stage`

![](/images/5-workshop/5.email/031-deploy-api.png?width=90pc)

Click **Deploy**

Save the **Invoke URL** for use in EC2

![](/images/5-workshop/5.email/032-deploy-api.png?width=90pc)

{{% notice warning %}}
**Save the Invoke URL:**
Copy this URL for use in section 4.6 Deploy EC2
{{% /notice %}}

You have completed setting up API Gateway! Next, proceed to [4.5.4 - Setup API Security](../4.5.4-setup-api-security).