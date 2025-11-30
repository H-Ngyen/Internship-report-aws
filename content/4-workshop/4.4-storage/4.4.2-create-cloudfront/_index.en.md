---
title : "Create CloudFront Distribution"
date :  "2024-01-01" 
weight : 2
chapter : false
pre : " <b> 4.4.2 </b> "
---

1. Access [CloudFront Console](https://console.aws.amazon.com/cloudfront/)

2. Click **Create distribution**

![](/images/5-workshop/4.s3/012-cloudfront.png?width=90pc)

3. At Distribution options section:

- **Distribution name:** `fcj-cloudfront-carbuyer`
- **Distribution type**: *Single website or app*

![](/images/5-workshop/4.s3/014-cloudfront.png?width=90pc)

4. Configure Origin:
- **Origin type**: Select `Amazon S3`
- **Origin domain**: Select `carbuyer-fcj-bucket.s3.ap-southeast-1.amazonaws.com`
- **Origin path**: Leave empty

![](/images/5-workshop/4.s3/013-cloudfront.png?width=90pc)

5. Configure Security:

- **Web Application Firewall (WAF)**: Select **Do not enable security protections**

![](/images/5-workshop/4.s3/015-cloudfront.png?width=90pc)

6. Review information and select **Create distribution**

![](/images/5-workshop/4.s3/016-cloudfront.png?width=90pc)

7. After deployment, copy **Distribution domain name** (format `d1234abcd.cloudfront.net`)

![](/images/5-workshop/4.s3/017-cloudfront.png?width=90pc)

8. Test CloudFront URL:

```
https://yourcloudfront.cloudfront.net/Database/danhgia/1760497475406-65792375.jpg
```
