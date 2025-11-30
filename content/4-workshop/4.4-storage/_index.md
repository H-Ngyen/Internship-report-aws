---
title : "Cấu hình S3 và CloudFront"
date :  "2024-01-01" 
weight : 4
chapter : false
pre : " <b> 4.4. </b> "
---

### Cấu hình S3 và CloudFront

Trong phần này, chúng ta sẽ thiết lập hệ thống lưu trữ và phân phối nội dung tĩnh cho ứng dụng CarBuyer sử dụng Amazon S3 và CloudFront CDN.

#### Giới thiệu về Amazon S3

Amazon S3 (Simple Storage Service) là dịch vụ object storage được thiết kế để lưu trữ và truy xuất bất kỳ lượng dữ liệu nào từ bất cứ đâu trên web.

**Ưu điểm chính:**

- **Độ bền cao** - 99.999999999% (11 nines) durability với automatic replication
- **Scalability** - Tự động scale để xử lý bất kỳ lượng dữ liệu nào
- **Cost-effective** - Chỉ trả tiền cho storage và bandwidth thực tế sử dụng
- **Security** - Hỗ trợ encryption, bucket policies, và access control lists
- **Integration** - Tích hợp tốt với CloudFront, Lambda, và các AWS services khác

#### Giới thiệu về Amazon CloudFront

Amazon CloudFront là Content Delivery Network (CDN) service phân phối nội dung đến người dùng với độ trễ thấp và tốc độ transfer cao.

**Ưu điểm chính:**

- **Global network** - Hơn 400 edge locations trên toàn cầu
- **Low latency** - Cache nội dung gần với người dùng cuối
- **Security** - Tích hợp với AWS Shield để chống DDoS attacks
- **Cost optimization** - Giảm bandwidth costs từ S3 origin
- **HTTPS support** - Free SSL/TLS certificates với AWS Certificate Manager

#### Kiến trúc Storage

Trong workshop này, chúng ta sẽ:

1. **Tạo S3 bucket** để lưu trữ static assets:
   - Hình ảnh sản phẩm xe ô tô (trong folder `Database/`)
   - Hình ảnh slider trang chủ (trong folder `SlideShow/`)
   - Các file media khác

2. **Cấu hình CloudFront distribution** để:
   - Cache và phân phối nội dung từ S3 origin
   - Giảm latency cho người dùng ở các khu vực khác nhau
   - Tối ưu bandwidth costs

{{% notice tip %}}
CloudFront sẽ cache nội dung tại edge locations, giúp giảm số lượng requests đến S3 và cải thiện performance đáng kể.
{{% /notice %}}

#### Nội dung

1. [Tạo S3 Bucket](4.4.1-create-s3/)
2. [Tạo CloudFront Distribution](4.4.2-create-cloudfront/)
