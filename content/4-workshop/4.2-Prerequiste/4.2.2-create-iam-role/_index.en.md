---
title : "Create IAM Role"
date :  "2024-01-01" 
weight : 2
chapter : false
pre : " <b> 4.2.2 </b> "
---

### Create IAM Role for EC2

In this section, we will create an **IAM Role** for EC2 instances to securely access AWS services.

#### Create IAM Role

1. Access **IAM** → **Roles** → **Create role**

![](/Internship-report-aws/images/5-workshop/2.prerequisite/014-createrole.png?width=90pc)

2. Select trusted entity type:
   - **Trusted entity type**: `AWS service`
   - **Use case**: `EC2`

![](/Internship-report-aws/images/5-workshop/2.prerequisite/015-createrole.png?width=90pc)

3. In the add permissions section, assign these policies under **Permissions policies**:
   - `AmazonDynamoDBFullAccess`
   - `AmazonS3FullAccess` 
   - `CloudFrontFullAccess`

![](/Internship-report-aws/images/5-workshop/2.prerequisite/016-createrole.png?width=90pc)

4. Name the role:
   - **Role name**: `carbuyer-ec2-role`
   - **Description**: `Role for EC2 to access AWS services`

![](/Internship-report-aws/images/5-workshop/2.prerequisite/017-createrole.png?width=90pc)

5. Select **Create role**

![](/Internship-report-aws/images/5-workshop/2.prerequisite/018-createrole.png?width=90pc)

6. Verify the created role

![](/Internship-report-aws/images/5-workshop/2.prerequisite/019-createrole.png?width=90pc)

Next, we will create IAM User and Access Keys for the application.