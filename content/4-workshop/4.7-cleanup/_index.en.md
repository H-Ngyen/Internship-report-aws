---
title : "Cleanup Resources"
date :  "2024-01-01" 
weight : 7
chapter : false
pre : " <b> 4.7. </b> "
---

### Cleanup Resources

After completing the workshop, you should delete the resources to avoid unexpected costs.

{{% notice warning %}}
Make sure you have backed up important data before deleting!
{{% /notice %}}

{{% notice info %}}
**Deletion order is important:**
Resources must be deleted in the correct order to avoid dependency errors.
{{% /notice %}}

#### 1. Delete Application Load Balancer

1. Access [EC2 Console](https://console.aws.amazon.com/ec2/) → **Load Balancers**

![](/images/5-workshop/7.cleanup/001-alb.png?width=90pc)

2. Select `carbuyer-alb`

![](/images/5-workshop/7.cleanup/002-alb.png?width=90pc)

3. Click **Actions** → **Delete load balancer**

![](/images/5-workshop/7.cleanup/003-alb.png?width=90pc)

4. Confirm by typing: `confirm`

![](/images/5-workshop/7.cleanup/004-alb.png?width=90pc)

5. Click **Delete**

![](/images/5-workshop/7.cleanup/005-alb.png?width=90pc)

{{% notice tip %}}
ALB must be deleted before Target Groups and EC2 instances.
{{% /notice %}}

#### 2. Delete Target Groups

1. In EC2 Console, select **Target Groups**

![](/images/5-workshop/7.cleanup/006-tg.png?width=90pc)

2. Delete each target group: `carbuyer-customer-tg`, `carbuyer-admin-employee-tg`

![](/images/5-workshop/7.cleanup/007-tg.png?width=90pc)

3. Select target group → **Actions** → **Delete**

![](/images/5-workshop/7.cleanup/008-tg.png?width=90pc)

4. Confirm

![](/images/5-workshop/7.cleanup/009-tg.png?width=90pc)

#### 3. Delete EC2 Instances

1. In EC2 Console, select **Instances**

![](/images/5-workshop/7.cleanup/010-ec2.png?width=90pc)

2. Select both instances: `carbuyer-customer-service`, `carbuyer-admin-service`

![](/images/5-workshop/7.cleanup/011-ec2.png?width=90pc)

3. Click **Instance state** → **Terminate instance**

![](/images/5-workshop/7.cleanup/012-ec2.png?width=90pc)

4. Confirm deletion

![](/images/5-workshop/7.cleanup/013-ec2.png?width=90pc)

{{% notice info %}}
Wait for instances to transition to **Terminated** state before continuing.
{{% /notice %}}

![](/images/5-workshop/7.cleanup/013-ec2-2.png?width=90pc)

#### 4. Delete NAT Gateway

1. Access [VPC Console](https://console.aws.amazon.com/vpc/) → **NAT Gateways**

![](/images/5-workshop/7.cleanup/014-nat.png?width=90pc)

2. Select `carbuyer-nat-gateway`

![](/images/5-workshop/7.cleanup/015-nat.png?width=90pc)

3. Click **Actions** → **Delete NAT gateway**

![](/images/5-workshop/7.cleanup/016-nat.png?width=90pc)

4. Confirm by typing: `delete`

![](/images/5-workshop/7.cleanup/017-nat.png?width=90pc)

5. Wait 2-3 minutes for NAT Gateway to be completely deleted

![](/images/5-workshop/7.cleanup/018-nat.png?width=90pc)

#### 5. Delete Elastic IP

1. In VPC Console, select **Elastic IPs**

![](/images/5-workshop/7.cleanup/019-eip.png?width=90pc)

2. Select Elastic IP created for NAT Gateway

![](/images/5-workshop/7.cleanup/020-eip.png?width=90pc)

3. Click **Actions** → **Release Elastic IP address**

![](/images/5-workshop/7.cleanup/021-eip.png?width=90pc)

4. Confirm

![](/images/5-workshop/7.cleanup/022-eip.png?width=90pc)

![](/images/5-workshop/7.cleanup/022-eip-2.png?width=90pc)

{{% notice warning %}}
Unattached Elastic IPs will be charged. Delete immediately after removing NAT Gateway!
{{% /notice %}}

#### 6. Delete API Gateway

1. Access [API Gateway Console](https://console.aws.amazon.com/apigateway/)

![](/images/5-workshop/7.cleanup/023-api.png?width=90pc)

2. Select API `carbuyer-email-api`

3. Click **Delete**

![](/images/5-workshop/7.cleanup/024-api.png?width=90pc)

4. Confirm by typing: `confirm`

![](/images/5-workshop/7.cleanup/025-api.png?width=90pc)

5. Click **Delete**

![](/images/5-workshop/7.cleanup/026-api.png?width=90pc)

#### 7. Delete Lambda Function

1. Access [Lambda Console](https://console.aws.amazon.com/lambda/)

![](/images/5-workshop/7.cleanup/028-lambda.png?width=90pc)

2. Select function `carbuyer-email-service`

![](/images/5-workshop/7.cleanup/029-lambda.png?width=90pc)

3. Click **Actions** → **Delete**

![](/images/5-workshop/7.cleanup/030-lambda.png?width=90pc)

4. Confirm by typing: `confirm`

![](/images/5-workshop/7.cleanup/031-lambda.png?width=90pc)

5. Click **Delete**

![](/images/5-workshop/7.cleanup/032-lambda.png?width=90pc)

#### 8. Delete CloudFront Distribution

1. Access [CloudFront Console](https://console.aws.amazon.com/cloudfront/)

![](/images/5-workshop/7.cleanup/033-cloudfront.png?width=90pc)

2. Select distribution `fcj-cloudfront-carbuyer`

![](/images/5-workshop/7.cleanup/034-cloudfront.png?width=90pc)

3. Click **Disable**

![](/images/5-workshop/7.cleanup/035-cloudfront.png?width=90pc)

4. Wait a few minutes for status to change to **Disabled**

![](/images/5-workshop/7.cleanup/036-cloudfront.png?width=90pc)

5. Select distribution, click **Delete**

![](/images/5-workshop/7.cleanup/037-cloudfront.png?width=90pc)

6. Confirm deletion

![](/images/5-workshop/7.cleanup/038-cloudfront.png?width=90pc)

{{% notice info %}}
CloudFront distribution must be **Disabled** before it can be deleted.
{{% /notice %}}

![](/images/5-workshop/7.cleanup/038-cloudfront-2.png?width=90pc)

#### 9. Delete S3 Bucket

1. Access [S3 Console](https://console.aws.amazon.com/s3/)

![](/images/5-workshop/7.cleanup/039-s3.png?width=90pc)

2. Select bucket `carbuyer-fcj-bucket`

3. Click **Empty** to delete all objects

![](/images/5-workshop/7.cleanup/041-s3.png?width=90pc)

4. Confirm by typing: `permanently delete`

![](/images/5-workshop/7.cleanup/042-s3.png?width=90pc)

5. Click **Empty**

![](/images/5-workshop/7.cleanup/043-s3.png?width=90pc)

6. Go back, select bucket and click **Delete**

![](/images/5-workshop/7.cleanup/044-s3.png?width=90pc)

7. Confirm by typing bucket name: `carbuyer-fcj-bucket`

![](/images/5-workshop/7.cleanup/045-s3.png?width=90pc)

8. Click **Delete bucket**

![](/images/5-workshop/7.cleanup/046-s3.png?width=90pc)

#### 10. Delete DynamoDB Tables

1. Access [DynamoDB Console](https://console.aws.amazon.com/dynamodb/)

![](/images/5-workshop/7.cleanup/047-dynamodb.png?width=90pc)

2. Select **Tables** from left menu

![](/images/5-workshop/7.cleanup/048-dynamodb.png?width=90pc)

3. Select table to delete: `DanhGia`, `DatLichKH`, `KieuDang`, `LoaiPhuKien`, `MauXe`, `NguyenLieuXe`, `PhuKien`, `Slider`, `ThuongHieu`, `TinTuc`, `User`, `XeOto`

4. Select table, click **Delete**

![](/images/5-workshop/7.cleanup/050-dynamodb.png?width=90pc)

5. Confirm by typing: `confirm`

![](/images/5-workshop/7.cleanup/051-dynamodb.png?width=90pc)

6. Verify result after deletion

![](/images/5-workshop/7.cleanup/052-dynamodb.png?width=90pc)

#### 11. Delete Security Groups

1. Access [EC2 Console](https://console.aws.amazon.com/ec2/) → **Security Groups**

![](/images/5-workshop/7.cleanup/053-sg.png?width=90pc)

2. Delete security groups: `carbuyer-customer-sg`, `carbuyer-admin-sg`

![](/images/5-workshop/7.cleanup/054-sg.png?width=90pc)

3. Select security group → **Actions** → **Delete security groups**

![](/images/5-workshop/7.cleanup/055-sg.png?width=90pc)

4. Confirm

![](/images/5-workshop/7.cleanup/056-sg.png?width=90pc)

5. Repeat the process to delete `carbuyer-alb-sg`

#### 12. Delete VPC Endpoints

1. Access [VPC Console](https://console.aws.amazon.com/vpc/) → **Endpoints**

![](/images/5-workshop/7.cleanup/057-enpoints.png?width=90pc)

2. Select endpoints to delete

3. Select endpoint → **Actions** → **Delete VPC endpoints**

![](/images/5-workshop/7.cleanup/059-enpoint.png?width=90pc)

4. Confirm

![](/images/5-workshop/7.cleanup/060-endpoint.png?width=90pc)

#### 13. Delete VPC

1. In VPC Console, select **Your VPCs**

![](/images/5-workshop/7.cleanup/061-vpc.png?width=90pc)

2. Select `carbuyer-fcj-vpc`

3. Click **Actions** → **Delete VPC**

![](/images/5-workshop/7.cleanup/063-vpc.png?width=90pc)

4. Confirm by typing: `delete`

![](/images/5-workshop/7.cleanup/064-vpc.png?width=90pc)

5. Click **Delete**

![](/images/5-workshop/7.cleanup/065-vpc.png?width=90pc)

{{% notice info %}}
Deleting VPC will automatically delete related resources: subnets, route tables, internet gateway.
{{% /notice %}}

#### 14. Delete IAM Roles

1. Access [IAM Console](https://console.aws.amazon.com/iam/) → **Roles**

![](/images/5-workshop/7.cleanup/066-role.png?width=90pc)

2. Select roles: `carbuyer-ec2-role`, `carbuyer-lambda-email-role`

3. Select **Delete**

![](/images/5-workshop/7.cleanup/068-role.png?width=90pc)

4. Confirm by typing: `delete`

![](/images/5-workshop/7.cleanup/069-role.png?width=90pc)

5. Click **Delete**

![](/images/5-workshop/7.cleanup/070-role.png?width=90pc)

#### 15. Delete IAM User

1. In IAM Console, select **Users**

![](/images/5-workshop/7.cleanup/071-user.png?width=90pc)

2. Select user `carbuyer-app-user`
3. Click **Delete**

![](/images/5-workshop/7.cleanup/073-user.png?width=90pc)

4. Select **Deactivate access key**

![](/images/5-workshop/7.cleanup/074-user.png?width=90pc)

5. Confirm and select **Delete user**

![](/images/5-workshop/7.cleanup/075-user.png?width=90pc)

#### 16. Delete Key Pair

1. Access [EC2 Console](https://console.aws.amazon.com/ec2/) → **Key Pairs**

![](/images/5-workshop/7.cleanup/076-keypair.png?width=90pc)

2. Select `carbuyer-keypair`

3. Click **Actions** → **Delete**

![](/images/5-workshop/7.cleanup/078-keypair.png?width=90pc)

4. Confirm

![](/images/5-workshop/7.cleanup/079-keypair.png?width=90pc)
