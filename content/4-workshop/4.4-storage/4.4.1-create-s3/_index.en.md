---
title : "Create S3 Bucket"
date :  "2024-01-01" 
weight : 1
chapter : false
pre : " <b> 4.4.1 </b> "
---

1. Access [S3 Console](https://console.aws.amazon.com/s3/)
2. Select **Create bucket**

![](/Internship-report-aws/images/5-workshop/4.s3/001-s3.png?width=90pc)

3. Configure bucket:

- **Bucket name**: `carbuyer-fcj-bucket`
- **AWS Region**: `ap-southeast-1`

![](/Internship-report-aws/images/5-workshop/4.s3/002-s3.png?width=90pc)

4. **Block Public Access settings for this bucket**: Uncheck **"Block all public access"** and confirm

![](/Internship-report-aws/images/5-workshop/4.s3/004-s3.png?width=90pc)

5. **Bucket Versioning**: Select **Enable** (to support future backups)

6. **Default encryption**: Select **SSE-S3**

7. **Bucket Key**: Select **Enable**

8. Click **Create bucket**

![](/Internship-report-aws/images/5-workshop/4.s3/005-s3.png?width=90pc)

9. Download image files from GitHub [here](https://github.com/khaizr0/RAB_Data/raw/refs/heads/main/Image.zip)

10. Select the bucket just created

![](/Internship-report-aws/images/5-workshop/4.s3/006-s3.png?width=90pc)

11. Select upload from machine and upload the 2 folders below:

![](/Internship-report-aws/images/5-workshop/4.s3/007-s3.png?width=90pc)

- `Database/`
- `SlideShow/`

![](/Internship-report-aws/images/5-workshop/4.s3/008-s3.png?width=90pc)

Click **Upload**

12. Configure Bucket Policy:

Select **Permissions** tab → **Bucket policy** → **Edit**

![](/Internship-report-aws/images/5-workshop/4.s3/009-s3.png?width=90pc)

Paste policy (replace `carbuyer-fcj-bucket` with your bucket name):

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::carbuyer-fcj-bucket/*"
    }
  ]
}
```

![](/Internship-report-aws/images/5-workshop/4.s3/010-s3.png?width=90pc)

13. Click **Save changes**

14. Check results:

Access an image file to verify:

```
https://carbuyer-fcj-bucket.s3.ap-southeast-1.amazonaws.com/Database/Products/[file-name].jpg
```

![](/Internship-report-aws/images/5-workshop/4.s3/011-s3.png?width=90pc)

{{% notice note %}}
Save the information:
- **Bucket name**: `carbuyer-fcj-bucket`
- **Region**: `ap-southeast-1`
{{% /notice %}}
