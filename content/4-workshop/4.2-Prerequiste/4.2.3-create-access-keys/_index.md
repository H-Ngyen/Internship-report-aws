---
title : "Tạo IAM User và Access Keys"
date :  "2024-01-01" 
weight : 3
chapter : false
pre : " <b> 4.2.3 </b> "
---

### Tạo IAM User và Access Keys

Chúng ta cần tạo IAM User với Access Keys để cả 2 ứng dụng Node.js (Customer và Admin) có thể truy cập DynamoDB và S3.

#### Tạo IAM User

1. Trong IAM Console, chọn **Users** → **Create user**

![](/Internship-report-aws/images/5-workshop/2.prerequisite/020-createuser.png?width=90pc)

2. Cấu hình user:
   - **User name**: `carbuyer-app-user`
   - **Provide user access to the AWS Management Console**: **KHÔNG chọn** (user này chỉ dành cho ứng dụng)

![](/Internship-report-aws/images/5-workshop/2.prerequisite/021-createuser.png?width=90pc)

3. Attach permissions policies:
   - `AmazonDynamoDBFullAccess`
   - `AmazonS3FullAccess`
   - `CloudFrontFullAccess`

![](/Internship-report-aws/images/5-workshop/2.prerequisite/022-createuser.png?width=90pc)

4. Xác nhận các thông tin và chọn **Create user**

![](/Internship-report-aws/images/5-workshop/2.prerequisite/023-createuser.png?width=90pc)

![](/Internship-report-aws/images/5-workshop/2.prerequisite/024-createuser.png?width=90pc)

#### Tạo Access Keys

1. Click vào user `carbuyer-app-user` vừa tạo

![](/Internship-report-aws/images/5-workshop/2.prerequisite/025-accesskeys.png?width=90pc)

2. Chọn tab **Security credentials**

![](/Internship-report-aws/images/5-workshop/2.prerequisite/026-accesskeys.png?width=90pc)

3. Scroll xuống phần **Access keys**, click **Create access key**

![](/Internship-report-aws/images/5-workshop/2.prerequisite/027-accesskeys.png?width=90pc)

4. Chọn use case: **Command Line Interface (CLI)**

![](/Internship-report-aws/images/5-workshop/2.prerequisite/028-accesskeys.png?width=90pc)

5. (**Optional**) Thêm description tag: `carbuyer-app-keys`

![](/Internship-report-aws/images/5-workshop/2.prerequisite/029-accesskeys.png?width=90pc)

6. Click **Create access key**

7. **Quan trọng:** Copy và lưu lại cả 2 thông tin:
   - **Access key ID**
   - **Secret access key**:

![30](/Internship-report-aws/images/5-workshop/2.prerequisite/030-collectkey.png?width=90pc)

8. Click **Download .csv file** để lưu credentials

9. Click **Done**

{{% notice warning %}}
**Cẩn thận:** Đây là lần duy nhất bạn có thể xem Secret Access Key. Nếu mất, bạn phải tạo access key mới. Đừng commit credentials vào Git hoặc chia sẻ công khai.
{{% /notice %}}

Tiếp theo, chúng ta sẽ tạo DynamoDB tables.