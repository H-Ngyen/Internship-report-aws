---
title : "Dọn dẹp tài nguyên"
date :  "2024-01-01" 
weight : 7
chapter : false
pre : " <b> 5.7. </b> "
---

### Dọn dẹp tài nguyên

Sau khi hoàn thành workshop, bạn nên xóa các tài nguyên để tránh phát sinh chi phí không mong muốn.

{{% notice warning %}}
Hãy chắc chắn bạn đã backup dữ liệu quan trọng trước khi xóa!
{{% /notice %}}

{{% notice info %}}
**Thứ tự xóa quan trọng:**
Cần xóa theo đúng thứ tự để tránh lỗi phụ thuộc giữa các tài nguyên.
{{% /notice %}}

#### 1. Xóa Application Load Balancer

1. Truy cập [EC2 Console](https://console.aws.amazon.com/ec2/) → **Load Balancers**

![](/images/5-workshop/7.cleanup/001-alb.png?width=90pc)

2. Chọn `carbuyer-alb`

![](/images/5-workshop/7.cleanup/002-alb.png?width=90pc)

3. Click **Actions** → **Delete load balancer**

![](/images/5-workshop/7.cleanup/003-alb.png?width=90pc)

4. Xác nhận bằng cách gõ: `confirm`

![](/images/5-workshop/7.cleanup/004-alb.png?width=90pc)

5. Click **Delete**

![](/images/5-workshop/7.cleanup/005-alb.png?width=90pc)

{{% notice tip %}}
Phải xóa ALB trước khi xóa Target Groups và EC2 instances.
{{% /notice %}}

#### 2. Xóa Target Groups

1. Trong EC2 Console, chọn **Target Groups**

![](/images/5-workshop/7.cleanup/006-tg.png?width=90pc)

2. Xóa từng target group: `carbuyer-customer-tg`, `carbuyer-admin-employee-tg`

![](/images/5-workshop/7.cleanup/007-tg.png?width=90pc)

3. Chọn target group → **Actions** → **Delete**

![](/images/5-workshop/7.cleanup/008-tg.png?width=90pc)

4. Xác nhận

![](/images/5-workshop/7.cleanup/009-tg.png?width=90pc)

#### 3. Xóa EC2 Instances

1. Trong EC2 Console, chọn **Instances**

![](/images/5-workshop/7.cleanup/010-ec2.png?width=90pc)

2. Chọn cả 2 instances: `carbuyer-customer-service`, `carbuyer-admin-service`

![](/images/5-workshop/7.cleanup/011-ec2.png?width=90pc)

3. Click **Instance state** → **Terminate instance**

![](/images/5-workshop/7.cleanup/012-ec2.png?width=90pc)

4. Xác nhận xóa

![](/images/5-workshop/7.cleanup/013-ec2.png?width=90pc)

{{% notice info %}}
Chờ instances chuyển sang trạng thái **Terminated** trước khi tiếp tục.
{{% /notice %}}

![](/images/5-workshop/7.cleanup/013-ec2-2.png?width=90pc)

#### 4. Xóa NAT Gateway

1. Truy cập [VPC Console](https://console.aws.amazon.com/vpc/) → **NAT Gateways**

![](/images/5-workshop/7.cleanup/014-nat.png?width=90pc)

2. Chọn `carbuyer-nat-gateway`

![](/images/5-workshop/7.cleanup/015-nat.png?width=90pc)

3. Click **Actions** → **Delete NAT gateway**

![](/images/5-workshop/7.cleanup/016-nat.png?width=90pc)

4. Xác nhận bằng cách gõ: `delete`

![](/images/5-workshop/7.cleanup/017-nat.png?width=90pc)

5. Chờ 2-3 phút để NAT Gateway bị xóa hoàn toàn

![](/images/5-workshop/7.cleanup/018-nat.png?width=90pc)

#### 5. Xóa Elastic IP

1. Trong VPC Console, chọn **Elastic IPs**

![](/images/5-workshop/7.cleanup/019-eip.png?width=90pc)

2. Chọn Elastic IP được tạo cho NAT Gateway

![](/images/5-workshop/7.cleanup/020-eip.png?width=90pc)

3. Click **Actions** → **Release Elastic IP address**

![](/images/5-workshop/7.cleanup/021-eip.png?width=90pc)

4. Xác nhận

![](/images/5-workshop/7.cleanup/022-eip.png?width=90pc)

![](/images/5-workshop/7.cleanup/022-eip-2.png?width=90pc)

{{% notice warning %}}
Elastic IP không gắn với instance sẽ bị tính phí. Nhớ xóa ngay sau khi xóa NAT Gateway!
{{% /notice %}}

#### 6. Xóa API Gateway

1. Truy cập [API Gateway Console](https://console.aws.amazon.com/apigateway/)

![](/images/5-workshop/7.cleanup/023-api.png?width=90pc)

2. Chọn API `carbuyer-email-api`

3. Click **Delete**

![](/images/5-workshop/7.cleanup/024-api.png?width=90pc)

4. Xác nhận bằng cách gõ: `confirm`

![](/images/5-workshop/7.cleanup/025-api.png?width=90pc)

5. Click **Delete**

![](/images/5-workshop/7.cleanup/026-api.png?width=90pc)

#### 7. Xóa Lambda Function

1. Truy cập [Lambda Console](https://console.aws.amazon.com/lambda/)

![](/images/5-workshop/7.cleanup/028-lambda.png?width=90pc)

2. Chọn function `carbuyer-email-service`

![](/images/5-workshop/7.cleanup/029-lambda.png?width=90pc)

3. Click **Actions** → **Delete**

![](/images/5-workshop/7.cleanup/030-lambda.png?width=90pc)

4. Xác nhận bằng cách gõ: `confirm`

![](/images/5-workshop/7.cleanup/031-lambda.png?width=90pc)

5. Click **Delete**

![](/images/5-workshop/7.cleanup/032-lambda.png?width=90pc)

#### 8. Xóa CloudFront Distribution

1. Truy cập [CloudFront Console](https://console.aws.amazon.com/cloudfront/)

![](/images/5-workshop/7.cleanup/033-cloudfront.png?width=90pc)

2. Chọn distribution `fcj-cloudfront-carbuyer`

![](/images/5-workshop/7.cleanup/034-cloudfront.png?width=90pc)

3. Click **Disable**

![](/images/5-workshop/7.cleanup/035-cloudfront.png?width=90pc)

4. Chờ vài phút cho status chuyển sang **Disabled**

![](/images/5-workshop/7.cleanup/036-cloudfront.png?width=90pc)

5. Chọn distribution, click **Delete**

![](/images/5-workshop/7.cleanup/037-cloudfront.png?width=90pc)

6. Xác nhận xóa

![](/images/5-workshop/7.cleanup/038-cloudfront.png?width=90pc)

{{% notice info %}}
CloudFront distribution phải ở trạng thái **Disabled** mới có thể xóa.
{{% /notice %}}

![](/images/5-workshop/7.cleanup/038-cloudfront-2.png?width=90pc)

#### 9. Xóa S3 Bucket

1. Truy cập [S3 Console](https://console.aws.amazon.com/s3/)

![](/images/5-workshop/7.cleanup/039-s3.png?width=90pc)

2. Chọn bucket `carbuyer-fcj-bucket`

3. Click **Empty** để xóa tất cả objects

![](/images/5-workshop/7.cleanup/041-s3.png?width=90pc)

4. Xác nhận bằng cách gõ: `permanently delete`

![](/images/5-workshop/7.cleanup/042-s3.png?width=90pc)

5. Click **Empty**

![](/images/5-workshop/7.cleanup/043-s3.png?width=90pc)

6. Quay lại, chọn bucket và click **Delete**

![](/images/5-workshop/7.cleanup/044-s3.png?width=90pc)

7. Xác nhận bằng cách gõ tên bucket: `carbuyer-fcj-bucket`

![](/images/5-workshop/7.cleanup/045-s3.png?width=90pc)

8. Click **Delete bucket**

![](/images/5-workshop/7.cleanup/046-s3.png?width=90pc)

#### 10. Xóa DynamoDB Tables

1. Truy cập [DynamoDB Console](https://console.aws.amazon.com/dynamodb/)

![](/images/5-workshop/7.cleanup/047-dynamodb.png?width=90pc)

2. Chọn **Tables** ở menu bên trái

![](/images/5-workshop/7.cleanup/048-dynamodb.png?width=90pc)

3. Chọn table muốn xóa: `DanhGia`, `DatLichKH`, `KieuDang`, `LoaiPhuKien`, `MauXe`, `NguyenLieuXe`, `PhuKien`, `Slider`, `ThuongHieu`, `TinTuc`, `User`, `XeOto`

4. Chọn table, click **Delete**

![](/images/5-workshop/7.cleanup/050-dynamodb.png?width=90pc)

5. Xác nhận bằng cách gõ: `confirm`

![](/images/5-workshop/7.cleanup/051-dynamodb.png?width=90pc)

6. Xác nhận kết quả sau khi xóa

![](/images/5-workshop/7.cleanup/052-dynamodb.png?width=90pc)

#### 11. Xóa Security Groups

1. Truy cập [EC2 Console](https://console.aws.amazon.com/ec2/) → **Security Groups**

![](/images/5-workshop/7.cleanup/053-sg.png?width=90pc)

2. Xóa các security groups: `carbuyer-customer-sg`, `carbuyer-admin-sg`

![](/images/5-workshop/7.cleanup/054-sg.png?width=90pc)

3. Chọn security group → **Actions** → **Delete security groups**

![](/images/5-workshop/7.cleanup/055-sg.png?width=90pc)

4. Xác nhận

![](/images/5-workshop/7.cleanup/056-sg.png?width=90pc)

5. Tiếp tục lặp lại thao tác để xóa `carbuyer-alb-sg`

#### 12. Xóa VPC Endpoints

1. Truy cập [VPC Console](https://console.aws.amazon.com/vpc/) → **Endpoints**

![](/images/5-workshop/7.cleanup/057-enpoints.png?width=90pc)

2. Chọn các endpoints cần xóa

3. Chọn endpoint → **Actions** → **Delete VPC endpoints**

![](/images/5-workshop/7.cleanup/059-enpoint.png?width=90pc)

4. Xác nhận

![](/images/5-workshop/7.cleanup/060-endpoint.png?width=90pc)

#### 13. Xóa VPC

1. Trong VPC Console, chọn **Your VPCs**

![](/images/5-workshop/7.cleanup/061-vpc.png?width=90pc)

2. Chọn `carbuyer-fcj-vpc`

3. Click **Actions** → **Delete VPC**

![](/images/5-workshop/7.cleanup/063-vpc.png?width=90pc)

4. Xác nhận bằng cách gõ: `delete`

![](/images/5-workshop/7.cleanup/064-vpc.png?width=90pc)

5. Click **Delete**

![](/images/5-workshop/7.cleanup/065-vpc.png?width=90pc)

{{% notice info %}}
Xóa VPC sẽ tự động xóa các tài nguyên liên quan: subnets, route tables, internet gateway.
{{% /notice %}}

#### 14. Xóa IAM Roles

1. Truy cập [IAM Console](https://console.aws.amazon.com/iam/) → **Roles**

![](/images/5-workshop/7.cleanup/066-role.png?width=90pc)

2. Chọn các roles: `carbuyer-ec2-role`, `carbuyer-lambda-email-role`

3. Chọn **Delete**

![](/images/5-workshop/7.cleanup/068-role.png?width=90pc)

4. Xác nhận bằng cách gõ `delete`

![](/images/5-workshop/7.cleanup/069-role.png?width=90pc)

5. Click **Delete**

![](/images/5-workshop/7.cleanup/070-role.png?width=90pc)

#### 15. Xóa IAM User

1. Trong IAM Console, chọn **Users**

![](/images/5-workshop/7.cleanup/071-user.png?width=90pc)

2. Chọn user `carbuyer-app-user`
3. Click **Delete**

![](/images/5-workshop/7.cleanup/073-user.png?width=90pc)

4. Chọn **Deactivate access key**

![](/images/5-workshop/7.cleanup/074-user.png?width=90pc)

5. Xác nhận và chọn **Delete user**

![](/images/5-workshop/7.cleanup/075-user.png?width=90pc)

#### 16. Xóa Key Pair

1. Truy cập [EC2 Console](https://console.aws.amazon.com/ec2/) → **Key Pairs**

![](/images/5-workshop/7.cleanup/076-keypair.png?width=90pc)

2. Chọn `carbuyer-keypair`

3. Click **Actions** → **Delete**

![](/images/5-workshop/7.cleanup/078-keypair.png?width=90pc)

4. Xác nhận

![](/images/5-workshop/7.cleanup/079-keypair.png?width=90pc)
