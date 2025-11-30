---
title : "Tạo CloudFront Distribution"
date :  "2024-01-01" 
weight : 2
chapter : false
pre : " <b> 4.4.2 </b> "
---

1. Truy cập [CloudFront Console](https://console.aws.amazon.com/cloudfront/)

2. Click **Create distribution**

![](/images/5-workshop/4.s3/012-cloudfront.png?width=90pc)

3. Tại phần Distribution options:

- **Distribution name:** `fcj-cloudfront-carbuyer`
- **Distribution type**: *Single website or app*

![](/images/5-workshop/4.s3/014-cloudfront.png?width=90pc)


4. Cấu hình Origin:
- **Origin type**: Chọn `Amazon S3`
- **Origin domain**: Chọn `carbuyer-fcj-bucket.s3.ap-southeast-1.amazonaws.com`
- **Origin path**: Để trống

![](/images/5-workshop/4.s3/013-cloudfront.png?width=90pc)


5. Cấu hình Security:

- **Web Application Firewall (WAF)**: Chọn **Do not enable security protections**

![](/images/5-workshop/4.s3/015-cloudfront.png?width=90pc)

6. Review các thông tin và chọn **Create distribution**

![](/images/5-workshop/4.s3/016-cloudfront.png?width=90pc)

7. Sau khi deploy xong, copy **Distribution domain name** (dạng `d1234abcd.cloudfront.net`)

![](/images/5-workshop/4.s3/017-cloudfront.png?width=90pc)

8. Test CloudFront URL:

```
https://yourcloudfront.cloudfront.net/Database/danhgia/1760497475406-65792375.jpg
```