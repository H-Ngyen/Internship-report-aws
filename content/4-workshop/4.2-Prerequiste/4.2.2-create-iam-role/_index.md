---
title : "Tạo IAM Role"
date :  "2024-01-01" 
weight : 2
chapter : false
pre : " <b> 4.2.2 </b> "
---
### Tạo IAM Role cho EC2

Trong phần này, chúng ta sẽ tạo **IAM Role** cho EC2 instances để truy cập các dịch vụ AWS một cách an toàn.

#### Tạo IAM Role

1. Truy cập **IAM** → **Roles** → **Create role**

![](/Internship-report-aws/images/5-workshop/2.prerequisite/014-createrole.png?width=90pc)

2. Chọn trusted entity type:
   - **Trusted entity type**: `AWS service`
   - **Use case**: `EC2`

![](/Internship-report-aws/images/5-workshop/2.prerequisite/015-createrole.png?width=90pc)

3. Ở phần thêm permission, ở phần **Permissions policies** hãy gán những policy này:
   - `AmazonDynamoDBFullAccess`
   - `AmazonS3FullAccess` 
   - `CloudFrontFullAccess`

![](/Internship-report-aws/images/5-workshop/2.prerequisite/016-createrole.png?width=90pc)

4. Đặt tên role:
   - **Role name**: `carbuyer-ec2-role`
   - **Description**: `Role for EC2 to access AWS services`

![](/Internship-report-aws/images/5-workshop/2.prerequisite/017-createrole.png?width=90pc)

5. Chọn **Create role**

![](/Internship-report-aws/images/5-workshop/2.prerequisite/018-createrole.png?width=90pc)

6. Xác minh lại role đã tạo

![](/Internship-report-aws/images/5-workshop/2.prerequisite/019-createrole.png?width=90pc)

Tiếp theo, chúng ta sẽ tạo IAM User và Access Keys cho ứng dụng.