---
title : "Create IAM User and Access Keys"
date :  "2024-01-01" 
weight : 3
chapter : false
pre : " <b> 4.2.3 </b> "
---

### Create IAM User and Access Keys

We need to create an IAM User with Access Keys so both Node.js applications (Customer and Admin) can access DynamoDB and S3.

#### Create IAM User

1. In IAM Console, select **Users** → **Create user**

![](/Internship-report-aws/images/5-workshop/2.prerequisite/020-createuser.png?width=90pc)

2. Configure user:
   - **User name**: `carbuyer-app-user`
   - **Provide user access to the AWS Management Console**: **DO NOT select** (this user is only for the application)

![](/Internship-report-aws/images/5-workshop/2.prerequisite/021-createuser.png?width=90pc)

3. Attach permissions policies:
   - `AmazonDynamoDBFullAccess`
   - `AmazonS3FullAccess`
   - `CloudFrontFullAccess`

![](/Internship-report-aws/images/5-workshop/2.prerequisite/022-createuser.png?width=90pc)

4. Confirm information and select **Create user**

![](/Internship-report-aws/images/5-workshop/2.prerequisite/023-createuser.png?width=90pc)

![](/Internship-report-aws/images/5-workshop/2.prerequisite/024-createuser.png?width=90pc)

#### Create Access Keys

1. Click on the `carbuyer-app-user` user just created

![](/Internship-report-aws/images/5-workshop/2.prerequisite/025-accesskeys.png?width=90pc)

2. Select **Security credentials** tab

![](/Internship-report-aws/images/5-workshop/2.prerequisite/026-accesskeys.png?width=90pc)

3. Scroll down to **Access keys** section, click **Create access key**

![](/Internship-report-aws/images/5-workshop/2.prerequisite/027-accesskeys.png?width=90pc)

4. Select use case: **Command Line Interface (CLI)**

![](/Internship-report-aws/images/5-workshop/2.prerequisite/028-accesskeys.png?width=90pc)

5. (**Optional**) Add description tag: `carbuyer-app-keys`

![](/Internship-report-aws/images/5-workshop/2.prerequisite/029-accesskeys.png?width=90pc)

6. Click **Create access key**

7. **Important:** Copy and save both pieces of information:
   - **Access key ID**
   - **Secret access key**:

![30](/Internship-report-aws/images/5-workshop/2.prerequisite/030-collectkey.png?width=90pc)

8. Click **Download .csv file** to save credentials

9. Click **Done**

{{% notice warning %}}
**Caution:** This is the only time you can see the Secret Access Key. If lost, you must create a new access key. Do not commit credentials to Git or share publicly.
{{% /notice %}}

Next, we will create DynamoDB tables.
