---
title : "Setup IAM Role & Lambda Function"
date :  "2024-01-01" 
weight : 1
chapter : false
pre : " <b> 4.5.1. </b> "
---

### Setup IAM Role & Lambda Function

In this section, we will create an IAM Role and Lambda function to handle email sending.

#### 1. Create IAM Role for Lambda on Console

Access [IAM Console](https://console.aws.amazon.com/iam/) → **Roles** → **Create role**:

![](/images/5-workshop/2.prerequisite/014-createrole.png?width=90pc)

#### 2. Select trusted entity

Select:
- **Trusted entity type**: `AWS service`
- **Use case**: `Lambda`

![](/images/5-workshop/5.email/007-trusted-entity.png?width=90pc)

#### 3. Attach permissions

Find and select policy: `AWSLambdaBasicExecutionRole`

![](/images/5-workshop/5.email/008-permissions.png?width=90pc)

#### 4. Name the role

- **Role name**: `carbuyer-lambda-email-role`
- **Description**: `Role for Lambda email service`

Click **Create role**

![](/images/5-workshop/5.email/009-role-name.png?width=90pc)

#### 5. Create Lambda function on Console

Access [Lambda Console](https://console.aws.amazon.com/lambda/) → **Create a function**:

![](/images/5-workshop/5.email/005-create-function.png?width=90pc)

**Choose function creation option:**
- Select **Author from scratch**

**Basic information:**
- **Function name**: `carbuyer-email-service`
- **Runtime**: Node.js 22.x
- **Architecture**: x86_64

![](/images/5-workshop/5.email/006-create-function.png?width=90pc)

**Permissions:**
- Click **Change default execution role**
- Select **Use an existing role**
- **Existing role**: `carbuyer-lambda-email-role`

Click **Create function**

![](/images/5-workshop/5.email/007-create-function.png?width=90pc)

#### 6. Download and upload deployment package

Download zip file from GitHub:
- [Download lambda-email-service.zip](https://github.com/khaizr0/RAB_Data/raw/refs/heads/main/lambda-email-service.zip)

In **Code** tab → **Upload from** → **.zip file**:
- Select `lambda-email-service.zip` file just downloaded
- Click **Save**

![](/images/5-workshop/5.email/006-upload-code.png?width=90pc)

#### 7. Configure Environment Variables

In **Configuration** tab → **Environment variables** → **Edit**:

![](/images/5-workshop/5.email/007-env-variables.png?width=90pc)

{{% notice info %}}
You can use Gmail SMTP or Amazon SES. In this workshop, we will use Gmail SMTP
{{% /notice %}}

Add environment variables:
- `EMAIL_HOST`: `smtp.gmail.com`
- `EMAIL_PORT`: `465`
- `EMAIL_USER`: `your-email@gmail.com` (replace with real email)
- `EMAIL_PASS`: `your-16-char-app-password` (Your App Password)

Click **Save**

![](/images/5-workshop/5.email/008-env-variables.png?width=90pc)

#### 8. Configure General settings

In **Configuration** tab → **General configuration** → **Edit**:

![](/images/5-workshop/5.email/008-1-env-variables.png?width=90pc)

- **Timeout**: 30 seconds
- **Memory**: 256 MB

Click **Save**

![](/images/5-workshop/5.email/008-general-config.png?width=90pc)

You have completed setup of IAM Role and Lambda function! Next, move to [4.5.2 - Test Lambda Function](../4.5.2-test-lambda).