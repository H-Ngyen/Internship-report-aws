---
title : "Tạo S3 Bucket"
date :  "2024-01-01" 
weight : 1
chapter : false
pre : " <b> 4.4.1 </b> "
---

1. Truy cập [S3 Console](https://console.aws.amazon.com/s3/)
2. Chọn **Create bucket**

![](/images/5-workshop/4.s3/001-s3.png?width=90pc)

3. Cấu hình bucket:

- **Bucket name**: `carbuyer-fcj-bucket`
- **AWS Region**: `ap-southeast-1`

![](/images/5-workshop/4.s3/002-s3.png?width=90pc)

4. **Block Public Access settings for this bucket**: Bỏ chọn **"Block all public access"** và tick xác nhận

![](/images/5-workshop/4.s3/004-s3.png?width=90pc)

5. **Bucket Versioning**: Chọn **Enable** (để hỗ trợ backup sau này)

6. **Default encryption**: Chọn **SSE-S3**

7. **Bucket Key**: Chọn **Enable**

8. Click **Create bucket**

![](/images/5-workshop/4.s3/005-s3.png?width=90pc)


9. Tải file ảnh từ GitHub [tại đây](https://github.com/khaizr0/RAB_Data/raw/refs/heads/main/Image.zip)

10. Chọn vào bucket vừa tạo

![](/images/5-workshop/4.s3/006-s3.png?width=90pc)

11. Chọn upload từ máy và upload 2 folder dưới đây:

![](/images/5-workshop/4.s3/007-s3.png?width=90pc)

- `Database/`
- `SlideShow/`

![](/images/5-workshop/4.s3/008-s3.png?width=90pc)

Click **Upload**


12. Cấu hình Bucket Policy:

Chọn tab **Permissions** → **Bucket policy** → **Edit**

![](/images/5-workshop/4.s3/009-s3.png?width=90pc)

Paste policy (thay `carbuyer-fcj-bucket` bằng tên bucket của bạn):

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

![](/images/5-workshop/4.s3/010-s3.png?width=90pc)

13. Click **Save changes**

14. Kiểm tra kết quả:

Truy cập một file ảnh để kiểm tra:

```
https://carbuyer-fcj-bucket.s3.ap-southeast-1.amazonaws.com/Database/Products/[tên-file].jpg
```

![](/images/5-workshop/4.s3/011-s3.png?width=90pc)

{{% notice note %}}
Lưu lại thông tin:
- **Bucket name**: `carbuyer-fcj-bucket`
- **Region**: `ap-southeast-1`
{{% /notice %}}
