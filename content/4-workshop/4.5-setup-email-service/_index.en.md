---
title : "Lambda Email Service"
date :  "2024-01-01" 
weight : 5
chapter : false
pre : " <b> 4.5. </b> "
---

### Lambda Email Service

In this section, we will deploy a serverless email notification service for the CarBuyer application using AWS Lambda and API Gateway.

#### Introduction to AWS Lambda

AWS Lambda is a serverless compute service that allows you to run code without managing servers. Lambda automatically scales and you only pay for actual compute time used.

**Key Advantages:**

- **Serverless** - No need to manage infrastructure, AWS automatically handles scaling and patching
- **Pay-per-use** - Pay only for invocations and compute time, no idle costs
- **Auto-scaling** - Automatically scales from a few requests to thousands per second
- **Event-driven** - Trigger from multiple sources like API Gateway, S3, DynamoDB
- **Free Tier** - 1 million free requests and 400,000 GB-seconds compute time per month

#### Introduction to Amazon API Gateway

Amazon API Gateway is a fully managed service to create, publish, maintain, monitor, and secure APIs.

**Key Advantages:**

- **RESTful APIs** - Supports REST API with HTTP methods (GET, POST, PUT, DELETE)
- **Security** - API Keys, IAM authorization, Lambda authorizers
- **Throttling** - Rate limiting to protect backend services
- **Monitoring** - Integrated with CloudWatch for metrics and logs
- **CORS Support** - Easy configuration of cross-origin requests

#### Email Service Architecture

In this workshop, we will:

1. **Create Lambda function** to:
   - Handle confirmation emails for test drive bookings
   - Send password reset emails
   - Use Gmail SMTP to send emails

2. **Create API Gateway REST API** to:
   - Expose Lambda function via HTTP endpoint
   - Configure API Key authentication
   - Deploy API to production stage

3. **Integrate with application** to:
   - Customer Service and Admin Service call API to send emails
   - Use API Key to secure requests

{{% notice info %}}
Lambda function will use Gmail SMTP. You need a Gmail account and create an App Password to use it.
{{% /notice %}}

#### Implementation Steps

1. [Setup IAM Role & Lambda Function](4.5.1-setup-iam-lambda/)
2. [Test Lambda Function](4.5.2-test-lambda/)
3. [Setup API Gateway](4.5.3-setup-api-gateway/)
4. [Setup API Security](4.5.4-setup-api-security/)

#### Important Information to Save

After completing the steps, save 2 important pieces of information for use in section 4.6:

**1. API Gateway Invoke URL** (from step 4.5.3):
```
https://YOUR_API_ID.execute-api.ap-southeast-1.amazonaws.com/prod
```

**2. API Key** (from step 4.5.4):
```
YOUR_GENERATED_API_KEY
```

{{% notice warning %}}
**Important Note:**
Both pieces of information will be used in the application's `.env` configuration file in section 4.6.
{{% /notice %}}
